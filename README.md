# MCMC Cosmological Parameter Estimation

This project estimates two key cosmological parameters- the **Hubble constant (H₀)** and the **matter density parameter (Ωm)** — using a custom implementation of the **Markov Chain Monte Carlo (MCMC)** method applied to observational Hubble parameter measurements.

---

## 📌 Overview

The notebook uses real observational data (`Hz_BC03_all.dat`) containing redshift `z`, Hubble parameter `H(z)`, and measurement errors `H_err`. A flat ΛCDM cosmological model is used to fit this data through Bayesian inference via MCMC sampling.

---

## 📓 Notebook Structure

### 1. Plotting the Measurements with Different Fits
Loads the observational Hubble parameter data and visualizes it alongside different model fits to understand the data distribution.

### 2. Defining Posterior and Proposal Functions
Defines the core Bayesian components:
- **Likelihood function** — based on chi-squared statistics
- **Uniform prior** — for both H₀ (50–100) and Ωm (0–1)
- **Posterior function** — product of likelihood and prior
- **Proposal function** — Gaussian random walk for parameter updates

### 3. MCMC Code
Implements the Metropolis-Hastings MCMC algorithm. Runs **5 independent chains** to sample the posterior distribution of H₀ and Ωm. Includes burn-in removal and chain visualization.

### 4. Efficiency and Convergence of Chains
- Computes the **acceptance rate** of each chain
- Checks **convergence** of H₀ and Ωm using the **Gelman-Rubin statistic (R̂)**

### 5. Density Plots of the Parameters & Confidence Levels
- 2D histogram of H₀ vs Ωm posterior samples
- Gaussian fits to the 1D marginal distributions
- **1σ confidence intervals** using the 16th and 84th percentiles

### 6. Plotting Model with Parameters Drawn from Posterior
Overlays 50 randomly drawn parameter sets from the posterior onto the observational data to visualize the model uncertainty.

### 7. Using a Gaussian Prior for Ωm
Repeats the full MCMC analysis using a **Gaussian prior** on Ωm (mean = 0.315, std = 0.007) instead of the uniform prior, and compares the resulting parameter estimates and chain convergence.

---

## 🛠️ Dependencies

```
numpy
matplotlib
scipy
```

Install them with:
```bash
pip install numpy matplotlib scipy
```

---

## 📂 Data

The notebook requires the file `Hz_BC03_all.dat` which should be placed in the same directory as the notebook. The file contains three columns:
- `z` — redshift
- `H(z)` — Hubble parameter measurement (km/s/Mpc)
- `H_err` — measurement uncertainty

---

## 📊 Results

The notebook produces posterior estimates of:
- **H₀** — Hubble constant (km/s/Mpc)
- **Ωm** — matter density parameter

with 1σ confidence intervals derived from the MCMC chains, under both uniform and Gaussian priors for Ωm.

---

## 🚀 How to Run

1. Clone this repository
2. Place the `Hz_BC03_all.dat` data file in the same folder
3. Open the notebook:
```bash
jupyter notebook Ex1P4.ipynb
```
4. Run all cells in order

---

## 📖 Background

This project is based on **Bayesian cosmological inference**. The Hubble parameter model used is derived from the flat ΛCDM framework:

$$H(z) = H_0 \sqrt{\Omega_m (1+z)^3 + (1 - \Omega_m)}$$

The MCMC sampler explores the parameter space using the **Metropolis-Hastings algorithm**, accepting or rejecting proposed steps based on the posterior probability ratio.
