-----------------------------------------------------------------------------------------------------------------------
Introduction:

Varicella, otherwise called Chickenpox, is an exceptionally infectious and normal
youth contamination among individuals around the world. In Hungary, it is
accounted for to have 36,000 to 45,000 cases each year, in any case, this is
probably going to be an underrated sum.
By and large, the infection is self-restricting, in any case, it might prompt serious
difficulties such as pneumonia, encephalitis, even in any case solid individuals
(Huber et al., 2020). Newborn children, elderlies and immunocompromised
individuals are at higher gamble of creating serious complexities from
Chickenpox. These complexities might be deadly.
This task intends to thoroughly examine the Chickenpox dataset by utilizing the
investigation strategies shrouded in the Time Series Examination course and
precisely anticipate the series for the next 10 units of time. This report
incorporates the illustrative investigation, appropriate perception, model
particular, model fitting and determination, analytic checking, and
understanding of the Hungary Chickenpox dataset.
-----------------------------------------------------------------------------------------------------------------------
Methods:

The Hungary Chickenpox dataset is a .csv expansion document that comprises of
week-by-week Chickenpox cases in Hungary between 2005 to 2015. It was
obtained from the UCI AI Store and stacked into Python.
A Dickey-Fuller Unit-Root Test (ADF) and the was performed and the chosen level
of significance for these tests is 0.05.
The analysis is done with the aid of TSA library, implementing the ACF, PACF,
SARIMA, and other libraries like numpy, pandas, statsmodels and Moving average
with the help of MS Excel. The results are then further analyzed to provide
insightful information.
-----------------------------------------------------------------------------------------------------------------------
Data Source:

The link for the time series data source is pasted herein below for the ready
reference.
Link: https://archive.ics.uci.edu/ml/datasets/Hungarian+Chickenpox+Cases
-----------------------------------------------------------------------------------------------------------------------
Results:

The Hungary Chickenpox dataset is aggregated across all cities in Hungary by
year. Research has found that chickenpox peaks during the spring season
(Rettner, 2019). Therefore, the dataset is further preprocessed and aggregated
from weekly data into monthly data. Monthly data is more informative when
determining the seasonality of the disease. The following are the results.
-----------------------------------------------------------------------------------------------------------------------
Data Exploration:

As the handled Hungary Chickenpox dataset just holds back one variable, the
time series model would incorporate just the quantity of chickenpox cases in
Hungary over the long haul.
-----------------------------------------------------------------------------------------------------------------------
Moving Average:

A moving average is a statistical method used to analyze data points by creating
a series of averages of different subsets of the full data set. We have used moving
average to smooth out short-term fluctuations and highlight longer-term trends.
This process is done with the help of tool Microsoft Excel. Excel file is shared
along with this report for your reference. The steps followed in that process are
mentioned below:

Steps followed for Moving Average in Excel (Shared in zipped folder):

1. It is noteworthy that the window size is the number of data points we
wanted to include in the moving average. A larger window size smooths
out the data more but may also delay the identification of trends or
patterns.
2. The moving average is calculated. To calculate the moving average, we
specified the window size and then take the average of the current data
point and the preceding data points within the window.
3. Plotted line graph to show all 3, 6 and 12-month moving average. Kindly
refer to color encoding mentioned in the below graph derived using MS
Excel, which shows 3, 6 and 12-month moving average.

Testing the Stationarity of the Dataset through ADF – Test:

Augmented Dickey Fuller test (ADF Test) is a common statistical test used to test
whether a given Time series is stationary or not. It is one of the most commonly
used statistical test when it comes to analyzing the stationary of a series.
Stationary is very important factor on time series. Augmented Dickey-Fuller Test
is done on the residue to determine is series is differenced nonstationary.

Taking Log Difference and doing ADF Test:

Transformation in time series data is done so that variance of time series can be
stabilized. Taking log difference of the number of cases taking difference as null.

Augmented Dickey-Fuller Test is again done after removing trend and
seasonality.

On perusal of the above code and the result of the same, it is clear that p-value
of the ADF test is greater than 0.05. Thus, time-series data is not stationary.
There is a trend or seasonality in the data that is causing the time series data to
change over time.
To identify pattern and trend in data Partial Autocorrelation and Correlation
done.
---------------------------------------------------------------------------------------------------------------------

Conclusion based on PACF and ACF Plots:

The ACF/PACF plots produced from this model helps to affirm the model’s ability
to capture the behavior. There is no longer a slowly decaying pattern seen in the
ACF plot, while the sizes of the significant ordinary lags are also smaller. The
plots also help confirm the series is now stationary and does not require ordinary
differencing.
--------------------------------------------------------------------------------------------------------------------

SARIMA Model:

After determining that our time series is stationary, I use the
SARIMA model to predict future values.
The model’s notation is SARIMA(p, d, q) (P, D, Q)lag. These three parameters
account for seasonality, trend, and noise in data. We will use the AIC (Akaike
information criterion) indicator which is an estimator of the relative quality of
statistical models. The lower the AIC value the better.
After performing multiple iterations, the model that gives AIC and BIC values
lowest is the best combination.

I have done certain iterations by changing the values in SARIMA
model as mentioned in the table stated herein below. By changing that I ave
derived the different values of AIC and BIC.
Also we have derived the Value of Mean Square Error and Root Mean Square Error.
For different teration of values in SARIMA Model, we got different values of MSE and RSME,
which is provided in the table given herein further after the code.

On Perusal of the above values derived from different iteration, I oncluded
that the best model is SARIMA (1,0,2)x(2,1,1)12, because the AIC and BIC are the
least.
-----------------------------------------------------------------------------------------------------------------------

Validating the Forecast:

To evaluate the model performance, I alculate the R-squared score and the
root mean square error of my dataset to test the authenticity of the model.
R Squared gives an indication of how well a model fits a given dataset. It
indicates how close the regression line (i.e the predicted values plotted) is to
the actual data values. The R squared value lies between 0 and 1 where 0
indicates that this model doesn’t fit the given data and 1 indicates that the
model fits perfectly to the dataset provided.
Root Mean Squared Error (RMSE) is the distance, on average, of a data point
from the fitted line, measured along a vertical line.
------------------------------------------------------------------------------------------------------------------------

Conclusion:

Based on the r2_score, which arrived at 89.76%, we concluded that the model
selected by us has 89.76% accuracy. The RMSE value of 0.3586 which is not high.
We can be confident about the model’s ability to predict Hungarian Chickenpox
in future.
