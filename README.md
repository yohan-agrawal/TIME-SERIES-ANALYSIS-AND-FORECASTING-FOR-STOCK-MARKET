Stock Price Prediction Using Time Series Models
This repository contains code for predicting stock prices using various time series models. The dataset used in this project is from NSE-TATAGLOBAL, which includes historical stock prices. The project demonstrates how to preprocess the data, check for stationarity, and apply different forecasting models including Moving Average, ARIMA, and SARIMA.

Table of Contents
Prerequisites
Data Import and Preprocessing
Stationarity Check
Model Fitting
Moving Average
ARIMA
SARIMA
Usage
License
Prerequisites
Make sure you have the following Python packages installed:

pmdarima
statsmodels
prophet
pandas-profiling
seaborn
numpy
matplotlib
sklearn
You can install these packages using pip:

pip install pmdarima statsmodels prophet pandas-profiling seaborn numpy matplotlib sklearn
Data Import and Preprocessing
Import Dataset

data = pd.read_csv(r'C:\Users\admin\Downloads\NSE-TATAGLOBAL.csv')
Convert Date Column and Reverse Data

data['Date'] = pd.to_datetime(data.Date, format='%Y-%m-%d')
data = data.iloc[::-1]
Set Date Column as Index

data.set_index('Date', inplace=True)
Stationarity Check
The stationarity of the time series is tested using the Augmented Dickey-Fuller (ADF) test. The series is transformed to make it stationary by applying a logarithmic transformation and differencing.

def test_stationarity(timeseries):
    # Transformation to make the data stationary
    timeseries_log = np.log(timeseries)
    timeseries_log_diff = timeseries_log.diff().dropna()
    
    # Plot rolling statistics and perform ADF test
    ...
Model Fitting
Moving Average
This section uses a moving average method for prediction. The performance is evaluated using Root Mean Squared Error (RMSE).

def moving_avg_prediction(data):
    ...
ARIMA
Auto ARIMA is used for forecasting stock prices. The model automatically selects the best parameters for ARIMA.

def arima_prediction(data):
    ...
SARIMA
The Seasonal ARIMA (SARIMA) model is used to capture seasonality in the time series. The model is fitted with parameters for both non-seasonal and seasonal components.

def sarima_prediction(data):
    ...
Usage
Load Data

data = pd.read_csv('your_data.csv', parse_dates=True, index_col='Date')
Run Forecasting Models

moving_avg_prediction(data)
arima_prediction(data)
sarima_prediction(data)
License
This project is licensed under the MIT License - see the LICENSE file for details.
