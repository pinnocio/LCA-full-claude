# LCA for Social Science Research: A Methodological Course

## Course Structure

This course consists of 12 RMarkdown modules (Modules 0–11) that provide a complete research design pipeline for conducting Latent Class Analysis in the social sciences. Each module is a standalone `.Rmd` file that can be knitted independently.

## Module Sequence

| Module | File | Content | Data |
|--------|------|---------|------|
| **0** | `Module_00_Setup.Rmd` | R environment setup, package installation, poLCA orientation | Self-contained |
| **1** | `Module_01_Research_Design.Rmd` | When to use LCA, research question formulation, theoretical framework | Self-contained (conceptual) |
| **2** | `Module_02_Indicators.Rmd` | Indicator selection, recoding, dimensional balance, sparseness | Self-contained (conceptual) |
| **3** | `Module_03_Sampling.Rmd` | Sample size, sampling strategy, ethics, data quality | Self-contained (conceptual) |
| **4** | `Module_04_Data_Preparation.Rmd` | Data import, simulation, cleaning, diagnostics, formula definition | **Creates** `lca_prepared_data.RData` |
| **5** | `Module_05_Estimation.Rmd` | EM algorithm, convergence, local maxima, random starts, sequential estimation | Loads prepared data; **creates** `lca_estimated_models.RData` |
| **6** | `Module_06_Selection.Rmd` | BIC/AIC/SABIC, elbow plots, BLRT, parsimony, decision framework | Loads models; **creates** `lca_selected_model.RData` |
| **7** | `Module_07_Classification.Rmd` | Entropy, ALCPP matrix, OCC, posterior probabilities | Loads selected model; **creates** `lca_diagnostics.RData` |
| **8** | `Module_08_Interpretation.Rmd` | Item-response probabilities, profile plots, naming fallacy | Loads selected model + diagnostics; **creates** `lca_interpretation.RData` |
| **9** | `Module_09_Validation.Rmd` | Construct validity, external validity, split-sample cross-validation | Loads all prior outputs |
| **10** | `Module_10_Covariates.Rmd` | Three-step approach, multinomial logistic regression, odds ratios | Loads all prior outputs |
| **11** | `Module_11_Reporting.Rmd` | Methods/results templates, required tables/figures, reviewer concerns, checklist | Loads all prior outputs |
| **12** | `Module_12_Extensions.Rmd` | LTA, RMLCA, Multiple-Group LCA, CCA, EGA | Self-contained (conceptual) |
| **13** | `Module_13_Applied_Lab.Rmd` | Guided analysis with real data (cheating, election), independent exercise, accessing ESS/GSS/ANES/WVS | Self-contained (uses poLCA built-in data) |
| **14** | `Module_14_Capstone.Rmd` | Four full research replications: Delinquency, Nationalism, SDOH, Health Behaviors by Gender | Self-contained (simulated replicas of published studies) |

## Data Flow

Modules 0–3 are self-contained (conceptual or setup only). Starting from Module 4, each module loads data saved by prior modules and saves its own outputs:

```
Module 4 → lca_prepared_data.RData
Module 5 → lca_estimated_models.RData (loads Module 4 output)
Module 6 → lca_selected_model.RData (loads Module 5 output)
Module 7 → lca_diagnostics.RData (loads Module 6 output)
Module 8 → lca_interpretation.RData (loads Modules 6-7 output)
Modules 9-11 → load all prior outputs
```

**Important:** Modules 4–11 must be knitted in order at least once to generate the `.RData` files. After the first pass, individual modules can be re-knitted independently as long as their required `.RData` files exist in the working directory.

## Requirements

- R (version 4.0+)
- RStudio (recommended)
- Packages: `poLCA`, `tidyverse`, `nnet`, `reshape2`, `knitr`, `kableExtra`, `haven`, `mice`

Install all packages:
```r
install.packages(c("poLCA", "tidyverse", "nnet", "reshape2", "knitr", "kableExtra", "haven", "mice"))
```

## Worked Example

A single worked example threads through the entire course: a study of political belief systems using six binary attitudinal indicators (redistribution, immigration restriction, national pride, institutional trust, traditional values, environmental regulation) measured on 800 simulated respondents drawn from four latent classes (Progressive, Conservative, Communitarian, Libertarian).

The simulation uses a known data-generating structure, which allows the course to demonstrate how well the analysis recovers the "true" classes — a pedagogical advantage not available with real data.

## Key References

- Collins, L. M., & Lanza, S. T. (2010). *Latent class and latent transition analysis.* Wiley.
- Weller, B. E., Bowen, N. K., & Faubert, S. J. (2020). Latent class analysis: A guide to best practice. *Journal of Black Psychology, 46*(4), 287–311.
- Linzer, D. A., & Lewis, J. B. (2011). poLCA: An R package for polytomous variable latent class analysis. *Journal of Statistical Software, 42*(10), 1–29.
