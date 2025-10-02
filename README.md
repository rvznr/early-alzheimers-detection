# Early Alzheimer Detection with MRI

This project focuses on **early detection and multi-class classification of Alzheimer’s Disease (AD)** using **MRI brain scans** and **deep learning (CNN - EfficientNetB0)**.  
The model can classify MRI images into four categories:  

- 🟢 **NonDemented**  
- 🟡 **VeryMildDemented**  
- 🟠 **MildDemented**  
- 🔴 **ModerateDemented**

---

## Dataset
The dataset used in this study is publicly available on Kaggle:  

 [Alzheimer’s Multiclass Dataset (Equal and Augmented)](https://www.kaggle.com/datasets/aryansinghal10/alzheimers-multiclass-dataset-equal-and-augmented)  

- Total images: **44,000 MRI scans**  
- Training: **35,200 images**  
- Validation: **8,800 images**  
- Balanced across 4 classes  

---

## Methodology

### Data Preprocessing
- Images resized to **128×128 (RGB)**  
- Applied **data augmentation** (Random Flip, Rotation, Zoom)  
- Dataset split: **80% training / 20% validation**  
- Seed fixed for reproducibility  

### Model Architecture
- Base model: **EfficientNetB0 (ImageNet pre-trained)**  
- Transfer Learning applied:  
  - **Warm-up stage:** Base frozen, classifier layers trained  
  - **Fine-tuning stage:** Base unfrozen, full model trained with low LR  
- Loss: `categorical_crossentropy`  
- Optimizer: `Adam`  

### Explainability
- Used **Integrated Gradients (IG)** for interpretability  
- Heatmaps show that the model focuses on **hippocampal and cortical regions**, aligning with clinical findings  

---

## Results

- **Validation Accuracy:** 82.8%  
- **Macro F1-score:** 0.83  
- **Macro ROC-AUC:** 0.96  

### Classification Report
| Class            | Precision | Recall | F1-score | Support |
|------------------|-----------|--------|----------|---------|
| MildDemented     | 0.879     | 0.811  | 0.844    | 2004    |
| ModerateDemented | 0.998     | 0.998  | 0.998    | 2037    |
| NonDemented      | 0.813     | 0.768  | 0.789    | 2576    |
| VeryMildDemented | 0.664     | 0.755  | 0.706    | 2183    |

**Overall Accuracy:** 82.8%  
**Macro Avg:** Precision 0.838 • Recall 0.833 • F1-score 0.834  
**Weighted Avg:** Precision 0.834 • Recall 0.828 • F1-score 0.830  
  

---

## Visual Examples

### Class Examples
<img width="611" height="163" alt="image" src="https://github.com/user-attachments/assets/34128cad-daf3-4a69-89c3-0597e7778a7c" />


### Integrated Gradients Heatmaps
<img width="522" height="221" alt="image" src="https://github.com/user-attachments/assets/8ce7743a-50dc-42c7-9622-d5357d09d714" />


---

## Future Work
- **Multi-center dataset integration:** Combine different Alzheimer MRI datasets for diversity  
- **Preprocessing standardization:** Apply skull-stripping, N4 bias correction, resampling, intensity normalization in a reproducible pipeline  
- **Explainability expansion:** Compare IG with Grad-CAM, Occlusion, and SHAP  

---

## Acknowledgements
- Dataset: [Kaggle – Alzheimer’s Multiclass MRI Dataset](https://www.kaggle.com/datasets/aryansinghal10/alzheimers-multiclass-dataset-equal-and-augmented)  
- Base model: EfficientNet (Tan & Le, 2019)  
- Libraries: TensorFlow, Keras, NumPy, Matplotlib, OpenCV
- Kaggle link: https://www.kaggle.com/code/ravzanursisik/early-alzheimer-detection-with-mri

---

## Citation

If you use this repository in your research or project, please cite it as:

**Şişik, R. N. (2025). Early Alzheimer Detection with MRI. GitHub repository.**  
Available at: [https://github.com/rvznr/early-alzheimers-detection](https://github.com/rvznr/early-alzheimers-detection)

---

## License

This project is open for everyone to use, modify, and share freely for educational and research purposes.  
No special permission is required, but please give proper credit by citing this repository if you use it in your work.

