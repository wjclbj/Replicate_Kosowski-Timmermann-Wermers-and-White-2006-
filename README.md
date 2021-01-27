# Replicate_Kosowski-Timmermann-Wermers-and-White-2006 with more recent data (up to 2020)

## The paper: 

[Kosowski, R., Timmermann, A., Wermers, R. and White, H. (2006), Can Mutual Fund “Stars” Really Pick Stocks? New Evidence from a Bootstrap Analysis. The Journal of Finance, 61: 2551-2595.](https://www.researchgate.net/publication/4913482_Can_Mutual_Fund_Stars_Really_Pick_Stocks_New_Evidence_from_a_Bootstrap_Analysis)

## Synopsis
The paper wants to test whether the estimated four-factor alphas of “star” mutual fund managers are due solely to luck or to genuine stock-picking skills.

In particular, it examines the statistical significance of the performance & performance persistence of the “best” and “worst” funds by a bootstrap procedure applied to a variety of unconditional and conditional factor models of performance.

The empirical results have shown that  the performance of these best and worst fund managers is not solely due to luck, that is, it cannot be
explained solely by sampling variability.
While the paper finds strong evidence of superior performance and performance persistence among growth-oriented funds using bootstrap tests for significance, no evidence of ability among managers of income-oriented funds. Inference using the bootstrap differs substantially from standard inference tests, especially in smaller samples of funds (or shorter time series) or among groups of funds with lower right-tail levels of performance.

## Data

All U.S. open-end domestic equity funds that have at least 60 monthly net return observations during the 1990 to 2020 period.

## Steps 
1. Perform a standard Carhart model using Fama-Macbeth rehression with Newey-West standard error adjustments.
![carhart](carhart_model.png)
  
2. Prepare for the boostrap. Use the Carhart model in step 1 to compute alphas, factor loadings and residues using the time series monthly return data of all funds available in the market.

3. For each fund, draw a sample w/ replacement from regression residues in the 2nd step, create a pseudo-time series of resampled residues. In this way, a pseudo monthly excess return are constructed
![bootstrap](bootstrap.png)

4. Regress the bootstrap returns for any b on Carhart factors. The result could be a positive alpha (skills) or a negative alpha (not so good). Repeat for each fund. 1000 iteration is performed for each bootstrap.

## Result (reproducing Table II of the paper, first three rows of Panel A & B)

The table below shows that
1. the median fund in the sample has an unconditional four-factor alpha of −0.07 per month (−0.84%, annualized), while the bottom and top funds have alpha estimates of −4.09% and 6.12% per month, respectively.

2. Funds with alphas ranked in the top decile (top 10%) generally exhibit significant bootstrapped p-values, but there are quantile points not as significant (top 4th, 5th, etc), indicating manager achieved it through luck alone. Looking at the correponding bootstrap p-values, indicating that extreme alphas are not ALWAYS significant.



|                                        	| Bottom 	|    2. 	|    3. 	|    4. 	|    5. 	|    1% 	|    3% 	|    5% 	|   10% 	|   20% 	|   30% 	|   40% 	| Median 	|   40% 	|  30% 	|  20% 	|  10% 	|   5% 	|   3% 	|   1% 	|   5. 	|   4. 	|   3. 	|   2. 	|    Top 	|
|---------------------------------------:	|-------:	|------:	|------:	|------:	|------:	|------:	|------:	|------:	|------:	|------:	|------:	|------:	|-------:	|------:	|-----:	|-----:	|-----:	|-----:	|-----:	|-----:	|-----:	|-----:	|-----:	|-----:	|-------:	|
|                    Unconditional Alpha 	|  -4.09 	| -2.95 	| -2.93 	| -2.86 	| -2.68 	| -1.00 	| -0.65 	| -0.49 	| -0.35 	| -0.23 	| -0.16 	| -0.11 	|  -0.07 	| -0.02 	| 0.02 	| 0.08 	| 0.16 	| 0.23 	| 0.29 	| 0.51 	| 4.19 	| 5.68 	| 6.11 	| 6.12 	| 118.19 	|
| Cross-sectionally Bootstrapped p-Value 	|   0.00 	|  0.00 	|  0.00 	|  0.01 	|  0.00 	|  0.00 	|  0.00 	|  0.06 	|  0.02 	|  0.00 	|  0.04 	|  0.28 	|   0.31 	|  0.62 	| 0.40 	| 0.30 	| 0.01 	| 0.03 	| 0.00 	| 0.11 	| 0.28 	| 0.10 	| 0.07 	| 0.08 	|   0.21 	|
|                     Parametric p-Value 	|   0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.01 	|  0.00 	|  0.07 	|  0.09 	|  0.01 	|  0.06 	|  0.28 	|   0.28 	|  0.61 	| 0.40 	| 0.31 	| 0.05 	| 0.05 	| 0.01 	| 0.02 	| 0.09 	| 0.09 	| 0.06 	| 0.07 	|   0.07 	|
|                  t-Unconditional Alpha 	|  -8.59 	| -8.06 	| -7.95 	| -7.83 	| -7.24 	| -3.89 	| -3.08 	| -2.73 	| -2.20 	| -1.64 	| -1.26 	| -0.88 	|  -0.54 	| -0.21 	| 0.19 	| 0.63 	| 1.23 	| 1.77 	| 2.14 	| 2.93 	| 4.21 	| 4.23 	| 4.25 	| 5.10 	|   5.87 	|
| Cross-sectionally Bootstrapped p-Value 	|   0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.02 	|  0.10 	|  0.08 	|  0.14 	|   0.25 	|  0.56 	| 0.39 	| 0.30 	| 0.09 	| 0.03 	| 0.01 	| 0.00 	| 0.00 	| 0.00 	| 0.00 	| 0.00 	|   0.00 	|
|                     Parametric p-Value 	|   0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.00 	|  0.01 	|  0.02 	|  0.04 	|  0.14 	|  0.20 	|   0.28 	|  0.57 	| 0.39 	| 0.29 	| 0.11 	| 0.04 	| 0.02 	| 0.00 	| 0.00 	| 0.00 	| 0.00 	| 0.00 	|   0.00 	|

* The First & Second row reports the linear regression estimate of monthly alphas of mutual funds RANKED ON CARHART ALPHA in % and cross-senctional bootstrapped p-value for alpha regression. The 3rd row reports the normal t-stats of alpha estimation. 

* Whereas the 4th-6th report the same metrics RANKED ON the t-stats of their CARHART ALPHA.

If jupyter notebook cannot be reviewed, please try paste the link into https://nbviewer.jupyter.org/.
