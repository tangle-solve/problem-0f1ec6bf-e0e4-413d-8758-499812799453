<!-- solve-problem:0f1ec6bf-e0e4-413d-8758-499812799453 -->
# Two-source extraction at the optimal leading entropy constant

A [Tangle Solve problem](https://solve.tangle.tools/problems/0f1ec6bf-e0e4-413d-8758-499812799453).

## What is the problem?

Construct an explicit two-source extractor Ext: {0,1}^n × {0,1}^n → {0,1} computable in polynomial time, such that for any pair of independent sources X, Y each with min-entropy at least k = log₂ n + O(1), the output is statistically close to uniform: |Ext(X,Y) − U₁| ≤ 0.01 (some fixed constant error).

Background: a source has min-entropy k if no string appears with probability more than 2^(−k). A random function is (with high probability) a two-source extractor for min-entropy k ≥ log n + O(1) — this is the information-theoretic threshold, since below ~log n even existence fails (counting argument: there aren't enough extractor functions). The open problem is an **explicit** (poly-time deterministic) construction matching this threshold: the entropy should be log n plus a *small absolute constant*, not merely O(log n) with a large or unspecified leading constant. Precise interpretation: achieve k = log₂ n + c for an explicit small constant c (ideally optimizing c). Ambiguity: some statements ask only for "O(1)" gap; the census title emphasizes the optimal *leading constant* (coefficient of log n should be 1).

## Why does it matter?

Two-source extractors at minimal entropy are the strongest known primitive on the path to explicit Ramsey graphs (an extractor for entropy log n + c yields bipartite Ramsey graphs of essentially optimal size) and to extracting from imperfect physical randomness with the weakest possible independence assumptions. Progress here historically drives the whole seeded-extractor and independence-extraction program (Chor–Goldreich, Raz, Bourgain, Zuckerman–Li line of work). Staying open blocks closing the classic explicit Ramsey graph problem at its optimal parameters.

## What's already known?

- Existence: a random function is a two-source extractor for min-entropy ≥ log n + O(1) with constant error (probabilistic method). This sets the target.
- Explicit constructions history: Chor–Goldreich (1985), Raz (2005, one source ≥ log² n), Bourgain (2005, both sources ≥ 0.499n, broke the "half entropy" barrier). A long line of work (Zuckerman, Li, Cohen, Chattopadhyay–Zuckerman, etc.) reduced entropy.
- Li (2023): explicit two-source extractors for k = O(log n) — asymptotically optimal order but with an unspecified/uncontrolled leading constant, and for general (non-balanced) entropy trade-offs. This is the best published result and the direct baseline.
- Techniques: residue-type samplers, non-malleable extractors, correlated-sample strategies, inner-product-based condensers. All current approaches lose constant factors; none is known to be lossless at the threshold.

## What would count as solving it?

A polynomial-time computable Ext with a proof that for all independent X, Y of min-entropy ≥ log₂ n + c, |Ext(X,Y) − U₁| ≤ ε (ε a fixed constant, e.g., 0.01), for an explicit absolute constant c (smaller c = stronger). Also valuable partial targets:
1. Any explicit construction with k = log₂ n + c for *some* explicit c (constant-gap, leading constant 1).
2. Lower-bound/barrier results: showing current techniques (e.g., inner product, non-malleable extractors via seeded extractors) cannot achieve c small.
3. Matching the existence threshold exactly (optimal c matching the probabilistic bound).

## How to start

1. Read Li (2023) fully, especially the reduction showing non-malleable extractors / correlated-sample extractors yield two-source extractors — the entropy loss per step is where the constant blows up; compute exactly where the O(log n) constant arises.
2. Study Bourgain's extractor and the Chattopadhyay–Zuckerman / Li non-malleable extractor chain to identify the entropy-loss lemmas (each loses a constant multiple of log n).
3. Main obstacle: every known composition step multiplies log n by a constant > 1; you need an additive-constant-loss condenser at the bottom. Consider entropy-surplus analysis of inner product on (log n + c)-bit "advice" chunks.
4. Try proving a barrier first — an impossibility result for natural proof strategies would itself be a contribution.

## Key references

- Xin Li, "Two Source Extractors for Asymptotically Optimal Entropy, and (Many) More," arXiv:2303.06802, FOCS 2023. Achieves explicit two-source extractors for min-entropy O(log n) via improved non-malleable extraction; the direct predecessor and baseline. https://arxiv.org/abs/2303.06802
- Bourgain (2005), "On the construction of affine extractors," and related two-source work — first construction beating entropy n/2 for two sources. (verify exact citation)
- Raz (2005), "Extractors with weak random seeds," STOC — two-source extraction when one source has entropy ≥ log² n. (verify)
- Chor–Goldreich (1985), "Unbiased bits from sources of weak randomness and probabilistic communication complexity" — defines the two-source extractor problem and gives early constructions. (verify)

## Warnings

- Distinguish "O(log n)" from "log n + O(1)": Li 2023 solves the former; this problem demands the latter. Do not conflate them.
- One-bit output with fixed constant error is the target; multi-bit output or (log n)-bit error demands are different (easier/harder respectively).
- The sources are general (not bit-fixing, not affine); constructions for structured sources do not count.
- Below entropy ~log n, extractors provably do not exist even non-explicitly — any claimed construction below that is wrong.
- "Explicit" means deterministic poly(n) time; quasipolynomial or advice-based constructions don't resolve the census problem.

---
*`ALGO-000056` · unverified*

## Acceptance guidance

A polynomial-time computable Ext with a proof that for all independent X, Y of min-entropy ≥ log₂ n + c, |Ext(X,Y) − U₁| ≤ ε (ε a fixed constant, e.g., 0.01), for an explicit absolute constant c (smaller c = stronger). Also valuable partial targets:
1. Any explicit construction with k = log₂ n + c for *some* explicit c (constant-gap, leading constant 1).
2. Lower-bound/barrier results: showing current techniques (e.g., inner product, non-malleable extractors via seeded extractors) cannot achieve c small.
3. Matching the existence threshold exactly (optimal c matching the probabilistic bound).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/0f1ec6bf-e0e4-413d-8758-499812799453?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000056.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000056)
