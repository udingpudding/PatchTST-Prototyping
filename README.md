# Patch-TST for Time-Series Demand Forecasting 📊⚡

## Background
My firm is building an ensemble of models for front-store demand forecasting. The goal was to prototype a transformer-based model, Patch-TST, to address slow training speeds 🐢 and poor performance on seasonal data 🌱, issues seen in the existing transformer-based model. The model was tested against TFT to assess training speed 🕒, overall performance 📈, and seasonal data handling 🌦️.

## Project Goals 🎯
- **Faster Training Speeds** than TFT ⚡
- **Par Overall Performance** to TFT 📊
- **Better Performance on Seasonal Data** 🌱

## Model Choice: Patch-TST 🧩
Patch-TST is designed to address traditional transformer limitations for time-series tasks:
- **Patching of Input Time-Series**: Sequential time-steps are grouped into patches, reducing the time complexity of transformers ⏳ and enabling larger lookback windows for better seasonal data handling 🌦️.
- **Channel Independence**: Each time-series is processed independently, allowing for better understanding of individual time-series without mixing data, which is beneficial for products with unrelated sales trends 📉📈.

## Model Development 🛠️
- **Libraries/Tools**: Developed using the TSAI library with FastAI for preprocessing. Optuna was used for hyperparameter tuning 🔧.
- **Dataset**: Oral Hygiene (Adversion B) was used for training and benchmarking against TFT 📚.
- **Forecasting Horizon**: Matched TFT’s for consistency 📅.

## Model Limitations ⚠️
1. **Exogenous Variables**: Patch-TST doesn’t support exogenous variables, limiting the feature set to auto-correlation only 🔍.
2. **Library Limitations**: TSAI library's limited documentation 📖 and lack of support for custom loss functions restricted testing 🚫.

## Model Results 📊
Despite faster training times 🕒, the model's performance was below expectations:
- **PatchTST Oral Hygiene**: Rolling SMAPE of 60%, with a training time of 90 seconds per epoch ⏱️.
- **TFT Oral Hygiene**: Rolling SMAPE of 37%, with a training time of >2 hours per total run ⏳.

## Explanation of Limitations 🧐
1. **Autocorrelation Assumption**: The absence of exogenous variables led to a significant loss of predictive power 📉.
2. **High Model Complexity**: The large number of parameters required and reduced input tokens due to patching led to overfitting and unstable training 🔴.
3. **Isolation of Input Time-Series**: Channel independence caused the model to ignore inter-relationships between time-series, reducing its predictive accuracy compared to TFT ❌.

## Going Forward 🚀
1. **Change Data Granularity**: Switching to daily data granularity may provide more data for better training 📅.
2. **Custom Loss Function**: Implementing SMAPE or weighted SMAPE could potentially improve performance ⚖️.
3. **Library Improvements**: Future updates to TSAI or adoption of other libraries could enable better handling of loss functions and model tuning 🔄.

## Project Summary 📝
Patch-TST was ruled out as a viable option for the ensemble due to poor performance despite faster training times. Further improvements to TFT and exploration of other advanced time-series forecasting methods like Mamba are recommended 🔍.
