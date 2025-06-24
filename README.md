
##  Lung Segmentation with U-Net

A deep learning project for lung image segmentation using a U-Net architecture trained on grayscale chest CT scans. The goal is to accurately segment lung regions from medical images to support further analysis or clinical decision-making.

---

### 📌 Project Description (Simple Version)

This project builds and trains a U-Net model to automatically detect and segment lung areas from grayscale chest CT images. The model was trained using medical image datasets (CT scans and corresponding segmentation masks), and it achieved high accuracy by learning pixel-wise classifications. This can be used in medical imaging applications like disease detection or monitoring lung conditions.

---

### 🧠 Model Overview

* **Architecture**: U-Net (encoder-decoder with skip connections)
* **Input**: Grayscale CT images (`512x512`)
* **Output**: Binary segmentation masks for lungs
* **Loss Function**: Binary Crossentropy
* **Optimizer**: Adam
* **Evaluation Metric**: Accuracy




---

### 📥 Data Preparation

* **Source**: Dataset downloaded via `gdown` from Google Drive.
* **Format**: Images and masks in `.bmp`, converted to `.png` for TensorFlow compatibility.
* **Splitting**: Train/validation split (85% / 15%) using `image_dataset_from_directory`.

---

### 🔁 Preprocessing & Augmentation

* Rescaling pixel values to `[0, 1]`
* Random flipping and rotation (for training set only)
* ImageDataGenerator used for augmentations to improve generalization

---

### 🏗️ Model Architecture

The U-Net model is composed of:

* **Downsampling blocks**: Conv → Conv → MaxPool
* **Bottleneck**: Two Conv layers
* **Upsampling blocks**: Transposed Conv → Concatenate with encoder output → Two Conv layers
* **Final layer**: 1×1 Conv with sigmoid activation

---

### 🏋️‍♀️ Training

* **Epochs**: 50 (with early stopping)
* **Batch Size**: 8
* **EarlyStopping**: Patience of 5, monitoring validation loss
* **Training Accuracy**: \~99.5%
* **Validation Accuracy**: \~99.6%

---

### 📊 Evaluation

* Accuracy: `~99.6%`
* Loss: `~0.01` on validation set

---

### 🖼️ Results & Visualization

* Plots of training vs validation accuracy and loss
* Visual comparison between:

  * Original grayscale CT scan
  * Ground-truth mask
  * Predicted mask

---

### 🚀 Future Improvements

* Add Dice Coefficient or IoU for evaluation
* Use post-processing (e.g., morphological operations) to refine predictions
* Test on different medical datasets (e.g., COVID-19 CT scans)

---

### ✅ Requirements

* Python 3.x
* TensorFlow / Keras
* NumPy, Pandas, Matplotlib, PIL
* gdown

---

