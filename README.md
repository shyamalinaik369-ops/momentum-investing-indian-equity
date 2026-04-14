# momentum-investing-indian-equity
Adaptive regime-aware momentum strategy for NSE Indian equity market · MSc Thesis · QMUL 2025
# Mitigating Momentum Crashes: An Adaptive, Regime-Aware Strategy for the Indian Equity Market

> MSc Dissertation · Data Analytics · Queen Mary University of London · 2025

---

## The Problem

Momentum investing — buying recent winners, avoiding recent losers — consistently beats the market over time. But it has one catastrophic flaw: during sudden market reversals, momentum strategies can lose **40%+ of their value in weeks**. During the COVID-19 crash of March 2020, a standard momentum strategy on the Indian market lost −26.3% in a single month, and −43.92% from its peak.

This thesis asked: **Can we keep momentum's return advantage while building a shield against its crashes?**

---

## Key Results

| Metric | Pure Momentum | ★ Adaptive Strategy |
|---|---|---|
| Total Return (10yr) | 1,613% | 862% |
| CAGR | 32.9% | 22.1% |
| Max Drawdown | −43.92% | **−17.14%** |
| Annualised Alpha | 21.15% | **10.87%** |
| Calmar Ratio | 0.75 | **0.98** |
| Market Beta | 1.21 | **0.49** |

The Adaptive Strategy has a lower total return than pure momentum — but that's intentional. It trades raw returns for dramatically better crash protection. Its **Calmar Ratio of 0.98** (return per unit of maximum loss) is the highest of all strategies tested, making it the most *efficient* use of risk in the entire research.

---

## Approach — 5 Strategies, Each Smarter Than the Last

The research was built layer by layer across five strategies:

**Strategy 1 — Pure Momentum (Baseline)**
Buy the top 10 Nifty 100 stocks by 12-month return each month. Extraordinary returns, catastrophic drawdowns.

**Strategy 2 — Sector Rotation + Beta Filter**
First identify the best sectors, then pick best stocks within them. Add a volatility filter excluding high-beta stocks. Safer, but lower returns.

**Strategy 3 — ML-Enhanced Selection**
Train Logistic Regression, Random Forest, and XGBoost to predict which stocks will outperform next quarter. Logistic Regression won — simpler models outperformed complex ones in noisy market data (a key finding in itself).

**Strategy 4 — K-Means Stock Clustering**
Cluster Nifty 100 stocks into archetypes by risk/return characteristics. The "Quality Momentum" cluster (low volatility, high consistency) provided superior risk-adjusted returns.

**Strategy 5 — Adaptive Regime-Aware (Final)**
Combine all layers with a market regime detector: in bull regimes, allocate aggressively to momentum; in bear/crash regimes, rotate defensively. Result: max drawdown cut from −43.92% to −17.14% while retaining meaningful alpha.

---

## Why the Simple ML Model Won

XGBoost and Random Forest memorised historical noise rather than learning genuine signal — a classic overfitting problem in financial data. Logistic Regression, with fewer parameters, was forced to focus on genuinely persistent signals (6-month returns, short-term volatility) rather than spurious patterns. **In noisy, non-stationary markets, simplicity and robustness beat complexity.**

---

## Tech Stack

| Tool | Usage |
|---|---|
| Python | Core analysis and backtesting |
| Pandas / NumPy | Data manipulation |
| Scikit-Learn | Logistic Regression, K-Means |
| XGBoost / LightGBM | Gradient boosted classifiers |
| SHAP | Model interpretability |
| QuantStats | Portfolio performance metrics |
| Matplotlib / Seaborn | Visualisation |
| Google Trends API | Sentiment signals |

---

## Data

- **Universe:** NSE Nifty 100 constituents
- **Period:** January 2015 – December 2024 (10 years, quarterly rebalancing)
- **Source:** Yahoo Finance (adjusted closing prices)
- **Features:** Price momentum, sector classification, beta, volatility, ML predictions, market regime signals

*Raw data files are not included in this repository due to size. See the notebook for data loading instructions using `yfinance`.*

---

## Repository Structure

```
momentum-investing-indian-equity/
├── thesis_momentum.ipynb     # Main analysis notebook
├── README.md
└── LICENSE
```

---

## How to Run

```bash
# Install dependencies
pip install pandas numpy scikit-learn xgboost lightgbm shap quantstats matplotlib seaborn yfinance

# Open notebook
jupyter notebook thesis_momentum.ipynb
```

---

## Key Insight

> *"The most efficient strategy is not the one with the highest return — it's the one with the best return per unit of risk taken. The Adaptive Strategy's Calmar Ratio of 0.98 makes it the most capital-efficient of all five approaches tested."*

---

## Author

**Shyamali Naik** · MSc Data Analytics · Queen Mary University of London · 2025

[LinkedIn](https://www.linkedin.com/in/shyamali-naik-91n78) · [Portfolio](https://YOUR-GITHUB-USERNAME.github.io)

---

*© 2025 Shyamali Naik. Licensed under MIT.*
