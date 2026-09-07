# EEG Motor Imagery Classification
This project explores the classification of left- and right-hand motor imagery using electroencephalography (EEG) data from the BCI Competition IV Dataset 2a. I developed a Python-based pipeline to preprocess EEG recordings, extract multiple types of signal features, and evaluate classical machine learning approaches across nine participants.
This project is focused on two main questions:
How does the choice of EEG feature representation affect motor imagery classification? & How does the classification performance vary across participants and machine learning models?
# Project Scope
This project was designed to explore EEG signal processing and motor imagery classification with machine learning models. The models were trained and evaluated within individual participants in the dataset rather than across participants. The analysis focuses on binary left-hand versus right-hand motor imagery classification.
## Dataset
The BCI Competition IV Dataset 2a contains EEG recordings from nine participants performing four motor imagery task: left hand, right hand, both feet, and tongue.
For this analysis, I focused on binary classification of left- and right-hand motor imagery. The recordings contain 22 EEG channels and 3 EOG channels sampled at 250 Hz.
The dataset is not included in this repository. 
## Tools
MNE-Python
NumPy
pandas
Matplotlib
scikit-learn
### Analysis Pipeline
Raw EEG -> Preprocessing -> Feature Extraction -> Classification -> Evaluation
### Preprocessing
- Left-hand and right-hand motor imagery trials were extracted from continuous EEG recordings and EOG channels were removed from the analysis.
- An 8-30 Hz Band Pass filter was applied.
- The motor imagery period for each trial was isolated.
### Feature Extraction
The three representations of EEG signals compared were Common Spatial Patterns (CSP), Band Power, and Hjorth Parameters.
CSP: captures spatial differences across EEG channels that discriminate between motor imagery conditions.
Band Power: measures the strength of signals in the mu (8-13 Hz) and beta (13-30 Hz) frequencies.
Hjorth Parameters: describes the time-domain properties of the EEG signal using activity, mobility, and complexity.
### Classification
The machine learning classifiers utilized included Linear Discriminant Analysis (LDA), Logistic Regression, Support Vector Machine (SVM), and Random Forest.
Each model was evaluated separately with a five-fold stratified cross validation.
## Results
Classifier choice produced relatively similar performance when CSP features were held constant. Mean accuracy across the nine participants ranged from 75.9% to 77.0% across the four classifiers.
Logistic Regression had the highest mean accuracy while holding CSP features constant with a value of 77.0%. It was followed closely by LDA (76.7%), SVM (76.6%), and Random Forest (75.9).
Feature extraction method and individual participant also influenced classification performance. CSP generally had the highest accuracy across participants while maintaining LDA as the classifier.

# Repository Structure
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_feature_extraction.ipynb
│   ├── 04_machine_learning.ipynb
│   └── 05_visualization.ipynb
│
├── figures/
│   ├── subject_classification_accuracy.png
│   ├── classifier_comparison.png
│   ├── feature_comparison.png
│   ├── feature_by_subject.png
│   ├── eeg_sensor_layout.png
│   └── csp_spatial_patterns.png
│
├── requirements.txt
└── README.md
