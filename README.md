# teachable-machine-classifier
# 🧠 Hands-On ML Exploration: Teachable Machine Classifier

## 📋 Project Overview
This project is an intuitive exploration of how data quality, volume, and composition directly impact how a machine learning model learns. Using **Google's Teachable Machine**, I trained a 2-category binary classifier using static file uploads to recognize and distinguish between two specific classes: **Pens** and **Mugs**.

## 🖼️ Submission: Trained Classifier
*   **Model Type:** Image Classifier (Standard MobileNet Architecture)

### Model in Action
*(Visual confirmation of my model predicting clean data versus breaking under noisy data)*

| Successful Prediction | Confused / Broken by Noisy Data |
| :---: | :---: |
| `![Clean Test Screenshot](success-screenshot.png)` | `![Noisy Test Screenshot](noisy-screenshot.png)` |

---

## 🔬 Experimentation & Observations

During training, I systematically varied the data inputs and introduced visual variations to test the boundaries of the model.

### 1. Data Quantity: Small vs. Medium Datasets
*   **The Test:** I initially evaluated training the model with only 1 sample image per class, then expanded the dataset to 7 diverse image samples per class.
*   **The Result:** With a single data sample, the model is mathematically brittle; it essentially memorizes that exact photo and cannot handle variations. Upgrading to 7 diverse samples containing different colors, styles, and angles of pens and mugs stabilized the output predictions, allowing the network to better recognize new items.

### 2. The Breaking Point: Introducing Noisy & Inconsistent Data
*   **The Test:** To simulate a messy real-world pipeline, I introduced inconsistent "noise" to the trained model by uploading completely unrelated visual shapes (like animals, vehicles, or complex textures) into the testing phase.
*   **The Result:** The model broke or yielded highly unpredictable outputs. Because it was only trained on a narrow set of clean pens and mugs against plain backgrounds, introducing a complex, unaligned image forced the model to make wild guesses or split its confidence score roughly 50/50, demonstrating a failure to generalize beyond its small training scope.

---

## 📑 3 Key Reflections on What Makes a Model Learn Better

### 💡 Observation 1: Feature Isolation Over Memorization
A machine learning model doesn't understand what a "mug" or "pen" is conceptually; it processes pixel arrays and contrast boundaries. If all training images feature items shot from a single angle, the model learns the specific layout rather than the core object. Varying angles forces the network to isolate true structural features.

### 💡 Observation 2: Background Consistency is a Double-Edged Sword
When training data uses perfectly clean white backgrounds, the model easily focuses on the object's silhouette. However, this creates a major vulnerability to ambient noise. If the model is deployed in a real-world environment with a busy background, it will often overfit to the background noise instead of tracking the target item.

### 💡 Observation 3: Overfitting Happens Rapidly with Low Sample Counts
With a small dataset (such as 7 samples per class), a model easily memorizes patterns instead of identifying broad rules. If 3 of the pen images happen to be red, the model might incorrectly assume that "redness" is a critical defining trait of a pen, causing it to misclassify a red mug later. True resilience requires extensive asset diversity.
