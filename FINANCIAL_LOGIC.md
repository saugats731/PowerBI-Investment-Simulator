# 🧠 Financial Concepts & Methodology

This document explains the financial formulas and metrics used in the Investment Simulator Dashboard.

## 1. Risk Metrics Explained

### **Beta ($\beta$)**
* **What it is:** A measure of how "wild" a stock is compared to the overall market (S&P 500).
* **Interpretation:**
    * **$\beta = 1.0$:** The stock moves exactly like the market.
    * **$\beta > 1.0$ (e.g., Nvidia at 1.76):** High Volatility. If the market goes up 1%, this stock likely goes up 1.76%. It offers higher reward but higher risk.
    * **$\beta < 1.0$ (e.g., Coca-Cola at 0.5):** Low Volatility/Defensive. If the market crashes, this stock falls less than the market.
    * **$\beta < 0$:** Inverse correlation (moves opposite to the market).

### **Alpha ($\alpha$)**
* **What it is:** The "Excess Return" earned above what was predicted by the risk taken. It measures the manager's skill or the stock's unique performance.
* **Interpretation:**
    * **Positive (+):** The stock beat the market expectation. (Value Created).
    * **Negative (-):** The stock underperformed its risk profile.
    * *Formula:* Actual Return - Expected Return (CAPM).

### **Sharpe Ratio**
* **What it is:** Measures "Return per unit of Risk." It answers: *Is the roller coaster ride worth the reward?*
* **Interpretation:**
    * **> 1.0:** Good (Acceptable return for the risk).
    * **> 2.0:** Very Good.
    * **< 1.0:** Poor (You are taking too much risk for too little profit).

### **R-Squared ($R^2$) & Scatter Plot**
* **Scatter Plot:** Visualizes the correlation. The X-axis is the Benchmark Return (S&P 500), and the Y-axis is the Stock Return.
* **$R^2$ (Correlation Strength):** Represents how much of the stock's movement is explained by the market.
    * **High $R^2$ (0.8 - 1.0):** The stock closely follows market trends (e.g., Index Funds).
    * **Low $R^2$ (0.0 - 0.3):** The stock ignores the market and does its own thing (e.g., Biotech, Crypto, or Unique Events).

---

## 2. The Simulation Model (CAPM)

The Investment Simulator uses the **Capital Asset Pricing Model (CAPM)** to estimate the "Expected Return" of an asset.

### **The Formula**
$$E(R_i) = R_f + \beta_i (E(R_m) - R_f)$$

### **The Elements**
1.  **$R_f$ (Risk-Free Rate):** The baseline return you could get with zero risk (e.g., a 10-Year US Treasury Bond). In this model, we use **4.2%**.
2.  **$E(R_m) - R_f$ (Market Risk Premium):** The extra reward investors demand for investing in the stock market instead of safe bonds. (Typically ~5-6%).
3.  **$\beta$ (Beta):** The multiplier that applies the premium to the specific stock.

### **Example Calculation**
If investing in a risky Tech Stock ($\beta = 1.5$) with a Market Premium of 8%:
* *Safe Return:* 4.2%
* *Risk Reward:* 1.5 * 8% = 12%
* **Total Expected Return:** 4.2% + 12% = **16.2%**

---

## 3. Future Value Projections
Once the **Expected Return ($r$)** is calculated via CAPM, we project wealth using the Compound Interest formula:

$$FV = P \times (1 + r)^n$$

* **$FV$:** Future Value (The result shown on the dashboard).
* **$P$:** Principal (Investment Amount set by slider).
* **$r$:** Expected Annual Return (from CAPM).
* **$n$:** Number of years (1 or 5).