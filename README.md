# Flight Price Prediction (Databricks)

I built this to get hands-on with Databricks. The notebook loads a flight booking dataset, explores it with SQL, and trains a few models to predict ticket prices.

Dataset: [Flight Price Prediction on Kaggle](https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction) (300,153 rows)

Tools: PySpark, SQL, scikit-learn, XGBoost, MLflow

## What the notebook does

1. Loads the data into Databricks and checks its quality.
2. Uses SQL to look at how price changes with travel class and how early the ticket is booked.
3. Prepares 37 features for modelling.
4. Trains three models on an 80/20 train/test split: linear regression, HistGradientBoosting and XGBoost.
5. Logs each run in MLflow (parameters, MAE, R2).

## What I found

- Economy tickets booked 1-7 days before departure cost about 2.4x more than ones booked 31+ days ahead.
- XGBoost cut the error by about 57% compared with the linear regression baseline.

| Model | MAE (Rs.) | R2 |
|---|---|---|
| Linear regression | 4,553 | 0.911 |
| HistGradientBoosting | 2,002 | 0.977 |
| XGBoost | 1,954 | 0.977 |

The two boosted models are very close. I used a single train/test split with no cross-validation, so I wouldn't say one is clearly better than the other.
