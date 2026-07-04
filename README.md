# Country-level Difference-in-Differences Analysis of Google AI Overviews

## Overview

This project investigates whether the March 2025 rollout of Google AI Overviews reduced Wikipedia pageviews across European countries.

Because AI Overviews were introduced gradually across countries rather than through a randomized experiment, the rollout creates a natural experiment suitable for a Difference-in-Differences (DiD) design.

Rather than focusing only on the final model, this repository documents the complete analytical workflow, including data preparation, diagnostic testing, control-group selection, model estimation, and sensitivity analyses.

## Research question

> Did the March 2025 rollout of Google AI Overviews reduce Wikipedia pageviews at the country level?

## Data

Daily country-level Wikipedia pageviews were collected from the Wikimedia REST API and aggregated to monthly observations.

Repository contents:

| File | Description |
|------|-------------|
| `country-level-ai-overviews-did.ipynb` | Complete research notebook |
| `country_daily_pageviews_wave4_wave5_candidates.csv` | Raw daily dataset |
| `country_daily_pageviews_wave4_wave5_candidates_fixed.csv` | Corrected dataset after recovering missing daily observations |

## Methodology

The analysis follows these steps:

1. Data collection from the Wikimedia REST API
2. Missing data recovery
3. Exploratory data analysis
4. Evaluation of France as a potential control country
5. Leave-one-out diagnostic analysis
6. Construction of an aggregate delayed-rollout control group
7. Difference-in-Differences estimation
8. Sensitivity analysis using a shorter post-treatment window

## Main findings

The analysis shows that:

- France is not an appropriate single control country because pre-treatment diagnostics reveal France-specific shocks.
- A control group based on delayed-rollout countries exhibits substantially better pre-treatment behavior.
- The estimated treatment effect is consistently negative (approximately −2% to −7%), but remains statistically insignificant across specifications.
- Confidence intervals include zero in every model.
- At the country level, the analysis does not provide evidence that the March 2025 rollout of Google AI Overviews produced a detectable reduction in Wikipedia pageviews.

## Key takeaway

The primary limitation appears to be the level of aggregation rather than the causal identification strategy.

Country-level pageviews are likely too coarse to detect localized traffic changes occurring at the article level, where AI Overviews are expected to have the strongest impact.

## Tech stack

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- Difference-in-Differences
- Fixed Effects Regression

## Project goals

This repository demonstrates an end-to-end causal inference workflow, including:

- natural experiment design
- Difference-in-Differences methodology
- diagnostic testing of identifying assumptions
- control-group construction
- robustness and sensitivity analysis
- reproducible research using Python
