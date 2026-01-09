# IEEE-CIS Fraud Detection (Classification)

End-to-end machine learning project structured from an exploratory notebook: data loading, preprocessing, feature engineering, model training, and evaluation for fraud classification.

## Problem
Predict whether an online transaction is fraudulent (`isFraud = 1`) using IEEE-CIS transaction + identity features.

## Dataset
This project expects the Kaggle **IEEE-CIS Fraud Detection** dataset files:
- `train_transaction.csv`
- `train_identity.csv`
(Optionally the test files if you extend inference.)

**Note:** Dataset files are not included in this repo. Place them in `data/raw/`.

## Quickstart

```bash
# 1) Create env
python -m venv .venv
# Windows: .venv\Scripts\activate
source .venv/bin/activate

# 2) Install deps
pip install -r requirements.txt

# 3) Put Kaggle files in:
# data/raw/train_transaction.csv
# data/raw/train_identity.csv

# 4) Train + evaluate
python scripts/train.py --data_dir data/raw --out_dir models
```

## Repository layout
- `notebooks/` — original notebook (reference)
- `src/` — reusable code (data prep, features, training)
- `scripts/` — CLI entrypoints (`train.py`, `predict.py`)
- `data/` — local-only data (gitignored)
- `models/` — saved models (gitignored)

## Metrics
For imbalanced fraud problems, prefer:
- ROC-AUC (primary)
- PR-AUC (optional)
- F1, Precision/Recall (threshold-dependent)

## Interview talk-track (suggested)
1. Problem framing (fraud = imbalanced classification, cost of FP/FN).
2. Data merge strategy (transaction + identity on `TransactionID`).
3. Missing values + encoding (imputation + categorical handling).
4. Baseline model (Decision Tree) and improved model (AdaBoost + class balancing).
5. Evaluation (holdout split, ROC-AUC, confusion matrix at chosen threshold).
6. Next steps (cross-val, leakage checks, calibration, XGBoost/LightGBM).

## License
MIT (change if needed).
