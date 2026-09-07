# ds351-data

Public datasets for **229351: Statistical Learning for Data Science 1**
(ว.วข. 351), Department of Mathematics, Chiang Mai University.

These files exist so that lab notebooks can fetch their data from a stable,
pinned URL. Always read them at a **commit SHA**, never from `main`:

```python
PIN = "<commit sha>"
URL = f"https://raw.githubusercontent.com/skitimo/ds351-data/{PIN}/elecequip.csv"
```

Pinning is what keeps a lab's numerical answers stable when this repository
changes later.

## Files

| File | Rows | Span | Frequency | Used by |
|---|---|---|---|---|
| `elecequip.csv` | 195 | 1996-01 to 2012-03 | monthly | Lec 07, Lab 07 |
| `AirPassengers.csv` | 144 | 1949-01 to 1960-12 | monthly | Lec 07, Lab 07 |
| `CarSales.csv` | 108 | 1960-01 to 1968-12 | monthly | Lec 07--09, Lab 08--09 |
| `CM_temp.csv` | 7882 | 1998-01-01 to 2019-07-31 | daily | Lec 08--09, Lab 08--09 |

### `elecequip.csv`

New orders index for the manufacture of electrical equipment (computer,
electronic and optical products) in the Euro area (17 countries), monthly,
2005 = 100.

This is the `elecequip` series of the R package `fpp2`, the dataset
*Forecasting: Principles and Practice* (2nd ed.) uses throughout its
decomposition chapter, FPP2 §6.1--6.3.

- Columns: an unnamed row number, `time` (`YYYY-MM`), `value`.
- Original source: Eurostat.

### `AirPassengers.csv`

Monthly totals of international airline passengers, 1949--1960, in thousands.
The classic Box & Jenkins series.

- Columns: `Month` (`YYYY-MM`), `Passengers`.
- Source: Rdatasets,
  <https://vincentarelbundock.github.io/Rdatasets/csv/datasets/AirPassengers.csv>.
  The decimal-year index of the original was converted to a plain monthly
  sequence and checked against it.

Its seasonal swing grows in proportion to the level of the series, which makes
it the honest example of when a **multiplicative** decomposition is needed.
Measured as the correlation between the annual level and the annual
peak-to-trough range, it scores `+0.991`, against `+0.433` for `CarSales` and
`+0.409` for `elecequip`.

### `CarSales.csv`

Monthly car sales in Quebec, January 1960 -- December 1968, in units. A standard
teaching series (Abraham & Ledolter, *Statistical Methods for Forecasting*).

- Columns: `Month` (`YYYY-MM`), `Sales`.

### `CM_temp.csv`

Daily maximum temperature in Chiang Mai, 1998-01-01 to 2019-07-31, in degrees
Celsius.

- Columns: `Date` (`YYYY-MM-DD`), `MaxTemp`.
- **Provenance not fully confirmed.** The file was published on a previous
  offering of this course (`donlapark.pages.dev/229351/data/CM_temp.csv`) with
  no attribution. It is most likely derived from Thai Meteorological Department
  station records, but that has not been verified with the original compiler.
  Treat it as a teaching dataset, not as a citable climate record.

Averaged to annual means it is the deck's simple-exponential-smoothing example:
21 points, a fitted \(\alpha\) of 0.314, and a trend of about
+0.07 °C/year that is real but too small for 21 years to justify modelling —
AICc prefers SES over Holt on it.

## Licence and use

These are long-published teaching datasets, redistributed here only so that a
course notebook has a stable URL to read. Rights remain with the original
sources named above. If you are one of those sources and would like a file
removed, please open an issue.
