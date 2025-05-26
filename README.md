**Credit Card Fraud Detection**

**Author: Revanth Pattipati**


**Executive Summary**

**Problem Overview**
Fraudulent transactions are rare but highly costly. With less than 0.2% of records labeled as fraud, this problem requires models that can detect anomalies with high recall and minimal false negatives. The goal was to evaluate multiple classification models, compare their performance on this imbalanced dataset, and draw actionable insights from the best-performing model.

<img width="382" alt="image" src="https://github.com/user-attachments/assets/39746b35-6ad4-4be0-a74e-6a507df8d13c" />

Random Forest clearly outperformed other models across every metric and had the lowest false negative count — making it the ideal choice for a high-risk use case like fraud detection.
Naive Bayes and Decision Tree had decent recall but made significantly more false positive predictions, which could increase operational cost.

**Modeling Approach**

**Models Used**
I trained and compared four supervised classification models:
- Logistic Regression with balanced class weights for interpretability
- Random Forest Classifier for high performance and feature insights
- Naive Bayes for baseline comparison
- Decision Tree for speed and transparency

**Evaluation Metrics Explained**
- Recall: Prioritized to minimize false negatives (missed fraud)
- Precision: Useful to control for false alarms
- F1 Score: Balanced view of recall and precision
- Confusion Matrix: Used to visualize FN/FP trade-offs


**Confusion Matrix Insights**
- Random Forest correctly predicted nearly all fraudulent transactions (TP = 17075, FN = 1)
- Logistic Regression had higher false positives (FP = 113), making it less optimal despite good F1
- Decision Tree offered a strong F1 but was not as robust overall
- Naive Bayes had the highest FP rate among all, despite 100% precision, indicating a possible imbalance sensitivity
  
**Feature Insights**
  
**Top features by importance (from Random Forest):**
- id (likely a leakage risk and should be removed in future versions)
- V14, V10, V12, V4 — all highly predictive of fraud, consistent with correlation findings
- Pairplot analysis confirmed clear class separation on these variables
**Note:** id contributing heavily suggests feature leakage. This was kept to demonstrate model capability but should be removed or masked in production use.

**Exploratory Data Analysis Summary**
- Strong class imbalance: ~492 frauds in 284,807 records (~0.17%)
- No nulls; only minor preprocessing required
- Correlation matrix highlighted key fraud predictors: V14, V4, V11, scaled_amount
- Pairplots revealed good class separability in selected features

**Next Steps & Recommendations**

**Short-Term Improvements**
- Remove id field from feature set in future iterations
- Perform GridSearchCV to fine-tune Random Forest hyperparameters
- Implement SMOTE/ADASYN or undersampling for robust balancing

**Future Exploration**
- Build and test ensemble stacking or gradient boosting models
- Implement real-time streaming fraud detection pipeline
- Use SHAP or LIME to improve explainability in production settings

**Project Artifacts**
- Jupyter Notebook: Final Analysis
- Dataset: Kaggle - Credit Card Fraud Detection

**Contact**

Revanth Pattipati

revanthpp@gmail.com

https://linkedin.com/in/revanthpp


