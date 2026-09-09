# Crypto exchange fee dataset

Published spot and futures fee schedules, leverage limits, KYC policy and fiat support for
8 major crypto exchanges — plus a dated snapshot of the 40 largest crypto assets.
Plain CSV and JSON. No sign-up, no API key, no rate limit.

| File | Rows | What it holds |
|---|---|---|
| [`data/exchange-fees.csv`](data/exchange-fees.csv) | 8 | Spot and futures maker/taker fees, max leverage, KYC, fiat currencies, per-category scores |
| [`data/exchange-fees.json`](data/exchange-fees.json) | 8 | Same rows plus source and licence metadata |
| [`data/coin-snapshot.csv`](data/coin-snapshot.csv) | 40 | Price, market cap, FDV, 24h volume, turnover %, ATH and drawdown, 30d/1y change, supply, exchange listings |
| [`data/coin-snapshot.json`](data/coin-snapshot.json) | 40 | Same rows plus source and licence metadata |

Always-current copies are generated at build time from the source of truth:
<https://cryptoflowcheck.com/data>

## Columns worth knowing about

- `spot_maker_taker` / `futures_maker_taker` — headline published rates, written as `maker / taker`.
  Volume tiers and token discounts can lower what you actually pay.
- `turnover_pct` — 24h volume divided by market cap. A liquidity ratio, not a signal:
  a large capitalisation with low turnover means the headline number is supported by
  coins that mostly do not move.
- `pct_from_ath` — how far below the all-time high the asset trades. Recovery is not
  symmetric: −90% needs +900% to get back to even.
- `listed_on` — which of the 8 compared exchanges carried a dollar spot market for that
  asset on the harvest date, space separated.

## Method and limits

- Exchange rows are transcribed by hand from each venue's own published fee page and
  re-checked on a fixed date. The date ships inside the JSON as `measured`.
- Asset rows come from the CoinGecko public API in a single harvest. They are a snapshot,
  not a live feed.
- The score columns (security, liquidity, ease of use, features, support) are editorial
  ratings on a 1–10 scale, not measurements. They are published so the ranking on the
  site can be checked, not because they are objective.
- No affiliate relationship influences a row. The files contain no referral links.
- Nothing here is investment advice.

## Licence

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Use it anywhere, including
commercially, with attribution:

```
Exchange fee data: CryptoFlowCheck (https://cryptoflowcheck.com/data), CC BY 4.0
```

## Related

Head-to-head pages and per-asset reference built on this same data:

- Exchange comparisons — <https://cryptoflowcheck.com/compare/exchanges>
- Write-ups derived from these files — <https://cryptoflowcheck.com/blog>
