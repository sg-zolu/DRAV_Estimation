# README: Supplementary Code for DRAV Estimation and Hypothesis Testing

## Overview
This README provides guidance for understanding and running the R code used to perform statistical analysis and data visualisation related to **Diving Respiratory Air Volume (DRAV)** estimation and its correlates in marine mammals.

The accompanying R Markdown file (`DRAV_Estimation_Hypothesis_Testing.Rmd`) contains:

1. **Data cleaning and preparation**
2. **Mixed-effects modelling of DRAV vs. dive behaviour and body density**
3. **Model selection using AIC and multimodel inference**
4. **Bootstrap-based confidence intervals and predictions**
5. **Sensitivity analyses across different drag coefficients**
6. **Visualisation of DRAV relationships and neutral buoyancy modelling**

---

## Folder Structure

The code expects the following file and folder organisation:

```
/Volumes/GEORGE_STORE/DRAV/
├── Vair_hypothesis_testing_0.02.csv
├── Vair_hypothesis_testing_0.03.csv
├── Vair_hypothesis_testing_0.04.csv
├── Vair_hypothesis_testing_0.05.csv
├── stroke_Vair_analysis_0.02.csv
├── stroke_Vair_analysis_0.03.csv
├── stroke_Vair_analysis_0.04.csv
├── stroke_Vair_analysis_0.05.csv
```

---

## R Package Dependencies
The following packages are required:
- `nlme` – for linear mixed-effects models
- `MuMIn` – for AIC-based model selection and R-squared values
- `forecast` – for time-series autocorrelation checks
- `boot` – for bootstrapping confidence intervals
- `ggplot2`, `ggpubr`, `ggeffects`, `gridExtra`, `ggnewscale` – for plotting
- `sjPlot` – for producing publication-ready model summary tables

Install them using:
```r
install.packages(c("nlme", "MuMIn", "forecast", "boot", "ggplot2", "gridExtra", "ggeffects", "ggpubr", "sjPlot"))
```

---

## Key Analyses

### 1. **Model of DRAV vs. Dive Depth and Body Density**
Mixed-effects models are used to estimate how DRAV varies with dive depth and body density (`BD`), using individual as a random effect. An AR(1) correlation structure accounts for temporal autocorrelation.

### 2. **Model Selection**
AIC weights from the `MuMIn::dredge()` function are used to select the best-fitting model, with support for models containing `max_depth`, `BD`, and their interaction.

### 3. **Bootstrapped Confidence Intervals**
Bootstrapping (via `boot::boot()`) is used to obtain 95% CI bands around model predictions.

### 4. **Data Visualisation**
Marginal effect plots show the relationship between DRAV and dive depth/body density.
Neutral buoyancy plots show how predicted DRAV values relate to the tissue density at which animals achieve neutral buoyancy at various depths.

### 5. **Sensitivity Analyses**
Model results are compared across datasets estimated using different drag coefficients (0.02 to 0.05). This ensures robustness of inference.

### 6. **Kinematic Correlation**
Linear mixed-effects models are used to relate DRAV to:
- Depth of stroke cessation
- RMS sway dynamic acceleration (stroking effort)

R-squared values (`r.squaredGLMM`) and model summaries are reported for each drag coefficient condition.

---

## Output Files
The script saves the following figure(s):
- `BD_Vair_ND_NEW_ggsave.png` – marginal effects of BD and depth on DRAV
- `NB_dep_lines.png` – DRAV vs. tissue density with neutral buoyancy contours

---

## Citation
If you use this code or reproduce parts of this analysis, please cite the associated manuscript and reference this repository.

---

## Contact
For questions, please contact [Your Name] at [your.email@example.com] or visit [lab website].


