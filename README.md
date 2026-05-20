# US Housing and Demographics Explorer

An interactive Streamlit dashboard for exploring residential demographic multipliers across U.S. states, built on 2017–2021 American Community Survey (ACS) data.

---

## Overview

This tool allows planners, researchers, and policymakers to explore how household composition — size, age distribution, school-age children, and public school enrollment — varies by housing type, tenure, size, and value across all 50 U.S. states and Washington D.C.

Demographic multipliers are derived from ACS microdata by **Professor Alexandru Voicu, College of Staten Island (CUNY)**.

---

## Features

- **State-level filtering** with an interactive map highlighting the selected state boundary
- **Housing type controls**: filter by housing age (All vs. Newer/2000–2021), structure type (single-family, multifamily), tenure (own vs. rent), bedroom count, and housing value tier
- **Three demographic data categories**:
  - Household Size (persons per unit)
  - School-Age Children (SAC, ages 5–17)
  - Public School Children (PSC)
- **Tabular data display** with columns dynamically selected based on the chosen demographic category
- **Downloadable glossary** (`.docx`) defining all ACS terms and housing classifications used in the app

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| `Streamlit` | Web app framework |
| `Pandas` | Data loading and filtering |
| `Pydeck` | Interactive map rendering |
| `GeoJSON` | U.S. state boundary geometries |

---

## Project Structure

```
├── main.py                                  # Main Streamlit application
├── gz_2010_us_040_00_5m.json                # GeoJSON file for U.S. state boundaries
├── DM_Overview_Quick_Guide_Glossary.docx    # Downloadable glossary and user guide
├── DM_{category}_{STATE}_{unittype}.csv     # ACS demographic multiplier data files
│   └── e.g. DM_pop_NEW JERSEY_ALLunits.csv
└── README.md
```

---

## Data File Naming Convention

CSV files follow this pattern:

```
DM_{category}_{STATE}_{unittype}.csv
```

| Parameter | Values |
|-----------|--------|
| `category` | `pop` (household size / persons by age), `sac` (school-age children), `psc` (public school children) |
| `STATE` | Uppercase state name, e.g. `NEW JERSEY`, `TEXAS` |
| `unittype` | `ALLunits` (all housing ages) or `NEWERunits` (built 2000–2021) |

---

## Setup and Installation

```bash
# Clone the repository
git clone https://github.com/umerfarooq7424/<repo-name>.git
cd <repo-name>

# Install dependencies
pip install streamlit pandas pydeck

# Run the app
streamlit run main.py
```

> **Note:** Ensure the GeoJSON file and all CSV data files are in the same directory as `main.py`.

---

## Usage

1. Select a **state** from the sidebar
2. Choose **housing age** (All or Newer built)
3. Select **structure type and tenure** (e.g. Single-Family Detached, Midsize Multifamily Rent)
4. Choose **bedroom count** and **housing value tier**
5. Pick a **demographic category** to display
6. The map highlights the selected state; the table below shows the filtered demographic data

---

## Data Source

American Community Survey (ACS) 5-Year Estimates, 2017–2021  
U.S. Census Bureau — [https://www.census.gov/programs-surveys/acs](https://www.census.gov/programs-surveys/acs)
