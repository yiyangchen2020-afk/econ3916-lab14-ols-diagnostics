# OLS Diagnostics: When the Standard Error Is Lying

## Objective

In this lab, I examined how heteroskedasticity, outliers, and model specification affect OLS regression estimates and standard errors.

## Methodology

- I simulated data with increasing error variance and compared classical and HC3 robust standard errors.
- I ran 400 simulations to compare the coverage rates of classical and robust confidence intervals.
- I examined four residual plots and used Breusch-Pagan and Jarque-Bera tests to check model assumptions.
- I used leverage, standardized residuals, and Cook's distance to identify influential observations.
- I fitted an OLS regression using California Housing data and compared classical and HC3 standard errors.
- I wrote a function called `hc3_se()` to calculate robust standard errors for selected coefficients.
- I simulated a regression with an omitted confounder to examine whether a model can pass diagnostic tests and still produce a biased estimate.

## Key Findings

The classical and HC3 regressions produced the same slope estimate of 2.0147. Their standard errors were 0.0264 and 0.0290, respectively.

In 400 simulations, the classical confidence interval covered the true slope 91.8% of the time, compared with 93.5% for the robust interval. Their Monte Carlo standard errors were 1.4% and 1.2%, respectively. The robust interval was closer to the nominal 95% coverage rate.

The residual plots showed different problems, including heteroskedasticity, missing curvature, and an outlier. The diagnostic tests helped identify some of these problems but did not detect every model issue.

After removing the most influential observation from a sample of 600, the slope changed by 0.58 of its standard error. The standard error decreased by 33%, from 0.0317 to 0.0213.

In the California Housing regression, the HC3 standard error on AveRooms was 5.02 times the classical standard error. My `hc3_se()` function returned 0.0121 for all districts and 0.0082 after excluding the 965 districts at the housing value ceiling.

In the Challenge, the estimated coefficient was 3.4215, compared with the true coefficient of 2.0000. The Breusch-Pagan and Jarque-Bera p-values were 0.4697 and 0.5599, respectively. The maximum Cook's distance was 0.0261. All three diagnostics passed, but the estimate was still biased because the model omitted a confounder.
