# news-ai-analysis

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

This project analyzes AI trends in Finnish news media.

## Project Organization

```
├── LICENSE            <- Open-source license if one is chosen
├── Makefile           <- Makefile with convenience commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default mkdocs project; see www.mkdocs.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata for
│                         news-ai-analysis and configuration for tools like black
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.cfg          <- Configuration file for flake8
│
└── news-ai-analysis   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes news-ai-analysis a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Scripts to download or generate data
    │
    ├── features.py             <- Code to create features for modeling
    │
    ├── modeling
    │   ├── __init__.py
    │   ├── predict.py          <- Code to run model inference with trained models
    │   └── train.py            <- Code to train models
    │
    └── plots.py                <- Code to create visualizations
```

---

## Initial Plan

### Data Acquisition

- **Tool**: finnish-media-scrapers
- **Target**: Yle news articles containing the keyword tekoäly from the past five years.
- **Commands**:
  fms-query-yle -q "tekoäly" -f2020-11-01 -t 2025-10-31 -o yle-tekoaly.csv

        fms-fetch-open -i yle-tekoaly.csv -o yle-tekoaly

        fms-html-to-text-yle -o yle_articles_output yle_articles

### Data Pre-Processing

- **Tool**: trankit
- **Model**: https://huggingface.co/uonlp/trankit/blob/main/models/v1.0.0/xlm-roberta-base/finnish.zip
- **Text Pre-Processing pipeline**:
  - Lowercase
  - Remove URLs and special characters
  - Tokenize
  - Lemmatize
  - POS tag
  - Remove stopwords

### Research questions

1. How has the frequency of tekoäly-related news evolved over time?

2. Main themes

   - TF-IDF
   - Topic modeling

3. How is AI framed — opportunity vs. threat?
