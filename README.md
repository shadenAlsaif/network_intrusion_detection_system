# 🛡️ AI-based Network Intrusion Detection System (NIDS)

This project implements a machine learning-based **Intrusion Detection System (IDS)** using the CIC-IDS-2017 dataset. It aims to classify network traffic as **benign or attack**, using advanced EDA, feature selection, and multiple classification models.

---

## 📁 Dataset
- **Source:** CIC-IDS-2017 (merged from 8 CSV files).
- **Samples used:** 500,000 (sampled from full dataset for faster training).
- **Classes:**
  - `BENIGN` → 0
  - `Attack` (any other label) → 1
- **Total features:** 79 numeric network-based features such as:
  - `Packet Length Std`, `Avg Bwd Segment Size`, `Init_Win_bytes_forward`, `Destination Port`, etc.

---

## 📊 Exploratory Data Analysis (EDA)
Key patterns found:
- **Class Imbalance:** 82% benign, 18% attack.
- **Packet Length Std** shows clear separation between classes.
- **Certain ports (80, 22)** are more likely linked to attacks.
- **Avg Bwd Segment Size** significantly differs between benign and attack traffic.

Plots included:
- Countplot (Benign vs Attack)
- Histograms and boxplots for important features
- Top destination ports
- Heatmap of top 20 selected features

---

## 🧪 Feature Selection
- Feature importance calculated using:
  - ✅ Random Forest
  - ✅ XGBoost
- Top 20 features selected based on **normalized average importance** across both models.
- Correlation analysis used to examine redundancy.

---

## ⚙️ Models Trained

| Model                | Accuracy | Precision | Recall | F1 Score |
|---------------------|----------|-----------|--------|----------|
| Random Forest        | **0.9964** | 0.9815    | 0.9992 | **0.9903** |
| XGBoost              | 0.9962   | 0.9793    | 0.9998 | 0.9894 |
| MLP Neural Network   | 0.9632   | 0.8510    | 0.9633 | 0.9037 |
| Logistic Regression  | 0.8865   | 0.6211    | 0.9394 | 0.7478 |

📈 ROC curves were plotted for all models.  
🎯 Random Forest and XGBoost achieved near-perfect AUC scores (>0.999).

---

## 📌 Key Techniques
- Data sampling from multiple CSVs
- Label binarization (`BENIGN` vs `Attack`)
- Feature scaling (`StandardScaler`)
- Balanced class weights to address imbalance
- Feature importance comparison using RF & XGB
- Visualization of confusion matrices and ROC curves

---

## 🧪 Evaluation Metrics
- Accuracy
- Precision
- Recall
- F1 Score
- ROC AUC
- Confusion Matrix

---

## 💡 Future Work
- Apply deep learning models (CNN/LSTM) to raw packet features
- Time-based modeling for sequential attack patterns
- Deploy as real-time intrusion detector using packet sniffers
- Extend to multiclass attack classification (DoS, PortScan, etc.)

---

## 📎 How to Run
```bash
# Clone the repo
git clone https://github.com/your_username/network_intrusion_detection_system.git
cd network_intrusion_detection_system

# Install required packages
pip install -r requirements.txt

# Open the notebook
jupyter notebook NIDS_project.ipynb

