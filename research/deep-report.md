# Deep research report

- Runs analysed: **29**
- Candidates per run: ~124
- Cumulative candidates evaluated: **3,794**
- Window: 2026-10-20 00:41:09+00:00 -> 2026-10-26 06:12:53+00:00

## Is the search actually working?

- Train-vs-holdout rank correlation: **0.4076** (min 0.1793, max 0.612, over 29 runs)
- Verdict: **search is informative**

> A correlation near 0 means the backtest ranking carries no information about future performance - the search is noise. Above 0.3 means the search genuinely finds something.

## Strategy families

| family | mean holdout CAGR | median | mean DD | mean DSR | max DSR | times basic | times gate |
|---|---|---|---|---|---|---|---|
| `sma_trend` | 20.9% | 22.1% | -16.3% | 0.154 | 0.203 | 319 | 0 |
| `sma_trend_vol_filter` | 14.9% | 14.3% | -10.4% | 0.129 | 0.569 | 970 | 0 |
| `sma_trend_efficiency` | 13.4% | 12.4% | -13.7% | 0.251 | 0.478 | 391 | 0 |
| `ema_trend` | 12.6% | 12.4% | -15.1% | 0.110 | 0.155 | 174 | 0 |
| `ema_trend_regime` | 9.4% | 9.4% | -11.1% | 0.061 | 0.187 | 239 | 0 |
| `sma_trend_slope` | 8.8% | 9.0% | -14.2% | 0.104 | 0.177 | 288 | 0 |
| `sma_trend_fast_slow` | 7.0% | 8.9% | -16.4% | 0.127 | 0.217 | 299 | 0 |
| `sma_trend_confirm` | 7.8% | 6.0% | -16.4% | 0.094 | 0.172 | 180 | 0 |
| `donchian_trend` | 2.4% | 1.7% | -4.2% | 0.302 | 0.429 | 58 | 0 |
| `donchian_trend_vol_filter` | 1.4% | 0.9% | -3.0% | 0.086 | 0.311 | 58 | 0 |
| `aapl_scalp_reversion` | 0.1% | 0.0% | -0.0% | 0.000 | 0.002 | 0 | 0 |
| `aapl_scalp_trend` | -5.0% | -2.7% | -4.0% | 0.037 | 0.215 | 3 | 0 |
| `sma_trend_rsi_filter` | -5.2% | -5.7% | -16.8% | 0.036 | 0.097 | 3 | 0 |

## Consistent winners (positive in every run seen)

| strategy | runs | positive | mean holdout | worst holdout | mean DSR | assets+ |
|---|---|---|---|---|---|---|
| `sma_trend_period200` | 29 | 29 | 30.7% | 28.1% | 0.150 | 9.5 |
| `sma_trend_vol_filter_period200_vol_lookback30_vol_max_pct4.0` | 29 | 29 | 30.2% | 27.4% | 0.410 | 8.5 |
| `sma_trend_period175` | 29 | 29 | 28.2% | 25.7% | 0.117 | 8.5 |
| `sma_trend_vol_filter_period175_vol_lookback30_vol_max_pct4.0` | 29 | 29 | 28.1% | 25.5% | 0.434 | 7.5 |
| `sma_trend_period50` | 29 | 29 | 27.7% | 25.5% | 0.193 | 8.5 |
| `sma_trend_vol_filter_period200_vol_lookback30_vol_max_pct3.0` | 29 | 29 | 27.3% | 25.0% | 0.146 | 9.5 |
| `sma_trend_period225` | 29 | 29 | 26.0% | 23.1% | 0.147 | 9.5 |
| `sma_trend_vol_filter_period100_vol_lookback30_vol_max_pct3.0` | 29 | 29 | 25.9% | 24.5% | 0.426 | 10.5 |
| `sma_trend_vol_filter_period225_vol_lookback30_vol_max_pct4.0` | 29 | 29 | 25.6% | 22.7% | 0.423 | 8.5 |
| `sma_trend_efficiency_period200_er_n30_er_min0.2` | 26 | 26 | 24.6% | 22.7% | 0.181 | 9.5 |

## Repeat overfits

| strategy | times | mean train | mean holdout |
|---|---|---|---|
| `sma_trend_fast_slow_slow_period250_fast_period10` | 29 | 6.9% | -4.7% |
| `sma_trend_efficiency_period250_er_n20_er_min0.3` | 25 | 6.8% | -1.4% |
| `sma_trend_fast_slow_slow_period150_fast_period10` | 20 | 5.0% | -1.8% |
| `sma_trend_confirm_slow_period150_fast_period50` | 12 | 12.7% | -0.7% |
| `sma_trend_confirm_slow_period100_fast_period20` | 12 | 10.1% | -0.7% |
| `sma_trend_slope_period100_slope_bars10` | 12 | 13.6% | -1.6% |
| `sma_trend_slope_period150_slope_bars40` | 12 | 13.2% | -3.4% |
| `sma_trend_confirm_slow_period100_fast_period50` | 4 | 10.9% | -0.2% |
| `aapl_scalp_trend_sma_period200_ema_period21_rsi_period14_rsi_max55` | 3 | -8.3% | -14.8% |
| `sma_trend_rsi_filter_period150_rsi_period14_rsi_max80` | 3 | 10.5% | -2.5% |

## What to try next

- KEEP: `sma_trend_period200` was positive in 29/29 runs (mean holdout 30.7%, worst 28.1%, mean DSR 0.150)
- KEEP: `sma_trend_vol_filter_period200_vol_lookback30_vol_max_pct4.0` was positive in 29/29 runs (mean holdout 30.2%, worst 27.4%, mean DSR 0.410)
- KEEP: `sma_trend_period175` was positive in 29/29 runs (mean holdout 28.2%, worst 25.7%, mean DSR 0.117)
- KEEP: `sma_trend_vol_filter_period175_vol_lookback30_vol_max_pct4.0` was positive in 29/29 runs (mean holdout 28.1%, worst 25.5%, mean DSR 0.434)
- KEEP: `sma_trend_period50` was positive in 29/29 runs (mean holdout 27.7%, worst 25.5%, mean DSR 0.193)
- FAMILY `sma_trend` has the best median holdout CAGR (22.1%) - add more parameters to it
- FAMILY `sma_trend_vol_filter` has the best median holdout CAGR (14.3%) - add more parameters to it
- FAMILY `sma_trend_efficiency` has the best median holdout CAGR (12.4%) - add more parameters to it
- FAMILY `ema_trend` has the best median holdout CAGR (12.4%) - add more parameters to it

