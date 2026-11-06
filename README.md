# quant-research

Research and backtesting of supply and demand strategies in FX, built to
answer one question honestly: does my edge hold up when discretionary
rules are turned into code and tested on data I haven't seen?

## Background

Since 2025 I have manually backtested 6,273 trades on the daily timeframe
across FX majors and crosses (plus gold and oil), from 2010 to 2026, over
19 versions of the strategy. Each version recorded a hypothesis, a test,
a result and what I changed next.

An earlier AI-assisted Python tool had a flaw: on daily candles it could
not tell whether the stop or the target was hit first, so results were
too optimistic. This project fixes that by using hourly data to resolve
the order of events within each daily candle.

## Roadmap

- [ ] **Setup:** repository, .gitignore, README, project structure
- [ ] **1. Data:** download hourly data, build daily candles (New York
      close), validate for gaps, duplicates and errors
- [ ] **2. Signals:** pivot and zone detection as testable functions
- [ ] **3. Execution engine:** resolve stop/target order with hourly data
- [ ] **4. Metrics:** win rate, expectancy, profit factor, max drawdown,
      longest losing streak
- [ ] **5. Validation:** test on held-out data, and compare daily-only
      vs. hourly resolution to measure the size of the candle flaw
- [ ] **6. Tests:** pytest throughout, not just at the end

## Repository structure

To be written as the project grows.

## Getting started

To be written.

## Data

Data files are not included in this repository: they are large, and the
providers' terms don't allow redistribution.

- **Main data:** hourly bid and ask prices from Dukascopy
- **Reference data:** OANDA daily candles from TradingView, the candles
  my manual backtest was done on, used to verify that my own daily
  candles match

Download instructions will be added in step 1.

## Findings

None yet. Results will be reported here, including the ones that don't
support the strategy.

## Known limitations

Known before writing any code:

- **Discretionary rules:** my manual rules involve judgement ("clear"
  structure, trap context). Turning them into code may lose part of the
  edge, and measuring how much is part of the project.
- **Overfitting:** the manual research tested many variables on
  overlapping periods, especially 2020–2026. Validation must use data
  that was not used to develop the rules.
- **Data source differences:** Dukascopy and OANDA prices differ
  slightly, so some trades will not match the manual backtest exactly.
- **Same-hour ambiguity:** hourly data reduces the candle problem but
  does not remove it. If stop and target are both hit within the same
  hour, the order is still unknown.

## Learning log

I document what I learn and the decisions I make in
[LEARNINGS.md](LEARNINGS.md).