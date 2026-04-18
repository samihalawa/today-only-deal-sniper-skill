---
name: today-only-deal-sniper
description: Turn a date and anchor neighborhood into a copy-paste-ready couples plan where each item is either time-exclusive for that date or a standing deal with verified TTL, discount, source, address, and walking distance. Use when the user wants a same-day Madrid deal plan with evidence, citations, and no padded evergreen filler.
---

# Today-Only Deal Sniper

Build a same-day leisure plan for Sami + Kitty, or a solo variant when partner mode is off.

Work evidence-first. Do not fabricate source coverage, user preferences, timing, addresses, discounts, or expiries.

## Defaults

- `date`: today in `Europe/Madrid`
- `anchor`: `Plaza del Callao`
- `partner_mode`: `Y`
- `budget_ceiling_eur`: `40`
- `walk_radius_min`: `15`
- `must_include`: `["cena", "cultura", "gratis"]`
- `must_exclude`: `[]`
- budget bias: prefer `>=30%` off or free

## Workflow

### 1. Memory Pass

Search the workspace sources that may contain leisure signals:

- Notion pages related to shared finances, plans, dining, or relationship routines
- Gmail receipts and booking confirmations for Groupon, TheFork, Atrápalo, Fever, Cinesa, museums, or restaurants
- Drive files with reservations, spending logs, or exported bank/account data
- Calendar events tied to meals, shows, museums, or couple plans

Produce a preference profile using citations for every claim. If a source is unavailable or yields little data, say so plainly.

Known seed facts to verify or preserve as prior signals:

- Groupon charge `-59,99 EUR` on `2025-09-25`
- joint-accounts page exists
- relationship-rules page exists
- explicit dining-habit data may be missing

### 2. Time-Exclusive Pass

Keep only items that match at least one hard filter:

- exists only on `date`
- expires within `<=24h` from `date`
- same-day promo tied specifically to that date
- free museum or public offer tied specifically to that date

Do not label standing promos as "today only".

### 3. Structured Deal Pass

Standing deals may be included only if all fields are verified:

- name
- address
- walking time from anchor
- exact discount or euro savings
- source URL
- expiry or TTL
- cuisine or activity type

Reject incomplete rows. Do not round or paraphrase discounts.

### 4. Couple-Widening Pass

Assemble the best day without padding weak slots:

1. mediodia cultural
2. comida
3. tarde plan
4. cena
5. nightcap

Skip any slot with no qualifying item.

### 5. Verification

Before finalizing, verify all of these:

- every item has a source URL and expiry
- no evergreen item is mislabeled as time-exclusive
- walking minutes are computed for each venue from the anchor
- inaccessible sources are logged explicitly
- ambiguous inputs are flagged instead of guessed
- the shortlist is copy-paste-ready and clean for WhatsApp or Notes

## Output Contract

Always return these six blocks in this order:

1. `Executive summary`
2. `Source ledger`
3. `Preference profile (evidence-only)`
4. `Spending / deal-platform evidence`
5. `Today's shortlist`
6. `Verification table`

The shortlist must use this one-line schema:

```text
HH:MM  Plan · Venue · Direccion · -X% (source, expira YYYY-MM-DD) · N min andando
```

## Hard Rules

- Flag ambiguity. Do not guess.
- Never fabricate source coverage.
- Time-exclusive is not the same as a standing promo.
- Couple mode is default, not mandatory.
- Respect higher-priority repo and system instructions.
