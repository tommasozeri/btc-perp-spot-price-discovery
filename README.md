# Who discovers the price of Bitcoin: spot or perpetual?

The Binance BTCUSDT perpetual and the BTCUSDT spot pair trade on the same venue, a few milliseconds apart. This note asks which of the two prices moves first, and how much of the permanent price variation each one originates, with a four-dimensional Hawkes process of their up and down moves.

**Paper:** [paper/btc-perp-spot-price-discovery.pdf](paper/btc-perp-spot-price-discovery.pdf) (8 pages).
A plain-language explanation in Italian is in [paper/btc-perp-spot-price-discovery-spiegazione.pdf](paper/btc-perp-spot-price-discovery-spiegazione.pdf).

## What it finds

- **The legs copy each other more than themselves.** An event is a move of at least half a basis point of the mid-price. Per parent event, each leg excites the other leg in the same direction more than it excites itself. The fitted process is stationary in every four-hour window (spectral radius 0.64 to 0.91).
- **The perpetual leads, moderately.** It leads because it moves more often, not because its moves are more contagious. Its Hawkes information share is 0.34 to 0.59 with all events as sources and 0.47 to 0.83 with exogenous events only. That agrees with the midpoint of the Hasbrouck bounds and with an event-time Hayashi–Yoshida lead–lag, computed on one day, in which the spot trails by about 50 ms.
- **Free spot trading flips the answer.** The four days of the sample inside Binance's zero-fee promotion on BTC spot pairs (December 2022 to March 2023) are the four days on which every measure reverses and the spot leads.

| Days | Hawkes information share of the perpetual |
|---|---|
| BTC, zero-fee spot (4 days) | 0.24 – 0.39 |
| BTC, from 2024 (7 days) | 0.34 – 0.59 |
| ETH (2 days) | 0.43 – 0.47 |

## Data and sources

Thirteen days between December 2022 and September 2026, eleven BTC and two ETH, best quotes at microsecond resolution from Tardis.dev. The quotes are licensed and are not in this repository. The estimation code is part of the author's master thesis and is not public yet.

`paper/src/` holds the LaTeX sources of the paper and of the Italian explanation and the CSV file behind the lead–lag figure. Build with `latexmk -xelatex paper.tex` from that folder.

## Limits

Thirteen days, the first of a month each: every statement is within a day. The four zero-fee days are also the four earliest days of the sample, so the sample alone cannot separate the fee regime from other differences of winter 2022–23. The spot stream has no exchange timestamp, which bounds the precision of the fastest reactions.

Based on the author's master thesis on Hawkes models of the perpetual–spot basis.
