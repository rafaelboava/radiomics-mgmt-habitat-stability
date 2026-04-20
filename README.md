# radiomics-mgmt-prediction 

This repository contains the complete pipeline for the non-invasive prediction of **MGMT** promoter methylation in Glioblastomas (GBM), utilizing peritumoral habitat radiomics.

## Overview
MGMT methylation is a critical biomarker for response to Temozolomide chemotherapy. This project investigates the hypothesis that the molecular signature of MGMT is manifested in the microstructural heterogeneity of the **peritumoral edema (FLAIR)**. We utilized a cohort of **577 patients** from the BraTS 2021 dataset to validate this prediction via Artificial Intelligence.

## Methodology
- **Data:** 577 cases from BraTS 2021 (RSNA-ASNR-MICCAI).
- **Feature Extraction:** `PyRadiomics` library following the IBSI standard.
- **Habitat Segmentation:** Comparative analysis between Peritumoral Edema (Label 2) and the Enhancing Core (Label 4).
- **Processing:** 215 radiomic features extracted per compartment, including First-order, Shape, and Texture matrices (GLCM, GLRLM, GLSZM).

## Performance Results (Benchmarking)
After testing different Machine Learning architectures, the **Support Vector Machine (SVM)** showed superior performance, outperforming tree-based models:

| Model | AUC (Area Under Curve) |
| :--- | :--- |
| **SVM (RBF Kernel)** | **0.640** |
| Random Forest | 0.579 |
| XGBoost | 0.572 |

### Key Findings:
1. **The Value of Edema:** Edema Entropy and Texture features were more consistent predictors than the features from the enhancing core.
2. **SVM Superiority:** SVM's ability to define decision boundaries in high-dimensional spaces proved ideal for the complexity of peritumoral radiogenomics.
3. **Scalability:** This model was validated in a robust multicentric cohort of 577 cases.

## Repository Structure
- `MGMT_Prediction_Pipeline.ipynb`: Notebook containing pre-processing, training, and benchmarking code.
- `requirements.txt`: List of dependencies for environment reproduction.
- `/results`: Confusion matrices and ROC curves.

## How to Run
1. Clone this repository.
2. Install the dependencies:
   ```bash
   pip install -r requirements.txt
