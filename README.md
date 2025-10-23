# Climate Zone Prediction from Weather Data: A Machine Learning Classification Problem
This is a university project created in collaboration with @[atpap](https://github.com/atpap)

## Overview
This project explores the use of Data Analysis and Machine Learning techniques to classify European cities into distinct climate zones based on real-time meteorological data. The primary goal is to develop an optimal classification model that requires minimal computational power, offering an alternative to traditional, complex physical weather models.

The problem is treated as a classification task. The final, optimized model achieved an F1-score of 0.7251, demonstrating good performance in predicting the climate zone from daily weather measurements.

## Key Project Decisions & Methodology
### Climate Zones
The model focuses on classifying cities across Europe into three simplified, broad climate categories, which are the most common on the continent, instead of the numerous, detailed Köppen classification zones :
- Mediterranean Climate (Csa, Csb)
- Oceanic Climate (Cfb, Cfc)
- Continental Climate (Dfa, Dfb, Dfc, Dfd, Dwc)

### Data Used
The model was trained using public meteorological data from "The Weather Dataset" available on Kaggle. Data from the year 2000 onwards was used to ensure consistency, reliability, and relevance to the effects of climate change.

Key weather measurements (features) selected for the model include:
- Minimum, Maximum, and Average Temperatures
- Precipitation (rain probability)
- Atmospheric Pressure
- Wind Speed and Direction

### Methodology Highlights
- Data Preprocessing: European cities were extracted from the global dataset and matched to a climate category using their geographical coordinates and an accurate Köppen map.
- Missing Value Handling: The project evaluated three different imputation strategies (mean, median, most frequent) to fill in missing weather data. The mean imputation strategy yielded the best results in the final models.
- Feature Engineering: New features, such as the Temperature Range (max_temp - min_temp) and a binary Rained variable, were created to potentially improve prediction accuracy.
- Feature Selection: The Recursive Feature Elimination with Cross-Validation (RFECV) method was used to automatically select the optimal subset of features for model training.
- Model Selection & Optimization: Multiple classification models (Logistic Regression, K-Nearest Neighbors, Random Forest, XGBoost) were tested. The final model was an XGBClassifier that was automatically optimized using the TPOTClassifier (AutoML) tool, which determined the best model and hyperparameters.

## Final Model Performance
The final model shows strong performance, particularly for the Continental Climate (Class 0), but relatively lower performance for the Oceanic Climate (Class 2), likely due to a smaller amount of training data for that zone.

## Future Work
- Advanced Model Tuning: Further hyperparameter tuning and exploration of other state-of-the-art classification algorithms.
- Data Scale: Rerunning the time-intensive optimization methods (like TPOT) on the entire dataset rather than a subset for potential accuracy gains.
- Comparison to Traditional Models: Conducting a detailed statistical comparison between this machine learning approach and traditional physical weather models.
