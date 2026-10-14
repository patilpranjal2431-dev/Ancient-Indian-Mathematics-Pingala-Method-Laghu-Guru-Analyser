# Pingala Laghu–Guru Analyser

A web-based Sanskrit prosody analyser that turns a shloka into its **Laghu (short) – Guru (long)** pattern and applies **Pingala's ancient binary method** to it, including the **Nāṣṭa** and **Uddiṣṭa** procedures, and detects classical meters such as **Anuṣṭubh** and **Triṣṭubh**.

> Pingala (c. 3rd–2nd century BCE) described, in the *Chandaḥśāstra*, a way of listing and finding every possible pattern of short and long syllables. This is, in effect, an early use of binary numbering. This project implements those rules as an interactive tool.

**Live demo:** _add your GitHub Pages / hosted link here_

---

## Why this project

Verse in Sanskrit is built from syllables of two kinds: **Laghu** (short, one unit) and **Guru** (long, two units). A line of *n* syllables can therefore take **2ⁿ** possible Laghu–Guru patterns. Pingala gave exact rules to:

1. **List** all 2ⁿ patterns in a fixed order (*Prastāra*).
2. Find the pattern at a given row number (**Nāṣṭa**, "the lost").
3. Find the row number of a given pattern (**Uddiṣṭa**, "the indicated").

This project makes those rules runnable, so you can test them on real verses and see how they connect to binary counting.

---

## Features

- Converts a shloka into its Laghu–Guru syllable pattern
- **Nāṣṭa:** given a row number, returns the Laghu–Guru pattern
- **Uddiṣṭa:** given a pattern, returns its row number
- Detects classical meters, including **Anuṣṭubh** (4 pādas × 8 syllables) and **Triṣṭubh** (4 pādas × 11 syllables)
- Interactive web interface (_describe your interactive feature here, e.g. a pattern explorer or practice mode_)

---

## The mathematics

**Convention used here:** the pattern is read left to right, and the table of all patterns starts with every syllable Guru (row 1) and ends with every syllable Laghu (row 2ⁿ).

**Uddiṣṭa (pattern → row number):**
1. Write the place values 1, 2, 4, 8, … under the syllables, left to right.
2. Add up the place values under the **Laghu** syllables.
3. Add 1. The result is the row number.

**Nāṣṭa (row number → pattern):**
1. Subtract 1 from the row number and write the result in binary, with the least significant bit first.
2. Read the bits left to right: **1 = Laghu**, **0 = Guru**.

**Worked example (n = 3, row 6):**

- Nāṣṭa: 6 − 1 = 5 = `101` in binary → bits (LSB first) 1, 0, 1 → **Laghu, Guru, Laghu**
- Uddiṣṭa check: Laghu at positions 1 and 3 → place values 1 + 4 = 5 → 5 + 1 = **6** ✓

**Why it matters:** Pingala's table is a binary counting system, and its row counts connect to Pascal's triangle and the Fibonacci sequence (through counting patterns by number of units).

> Check that this section matches the convention used in your code. If your Laghu/Guru bit assignment or row order differs, update the text so the README and the code agree.

---

## Getting started

This is a static web app (HTML/JavaScript), so there is nothing to install.

```bash
git clone https://github.com/patilpranjal2431-dev/Ancient-Indian-Mathematics-Pingala-Method-Laghu-Guru-Analyser.git
cd Ancient-Indian-Mathematics-Pingala-Method-Laghu-Guru-Analyser
# then open index.html in your browser
```

## How to use

1. Paste or type a shloka into the input box (_state the supported script, e.g. Devanagari or IAST_).
2. Read the Laghu–Guru pattern and the detected meter.
3. Use the Nāṣṭa and Uddiṣṭa sections to look up a pattern from a row number, or a row number from a pattern.

_Add 1–2 screenshots here, e.g. `![Analyser screenshot](screenshot.png)`._

---

## Testing

_List a few cases you have checked, for example:_

- Row 1 for *n* = 3 is all Guru, and row 8 is all Laghu.
- Nāṣṭa(Uddiṣṭa(p)) returns the original pattern *p* for every pattern of length 1 to 8.
- Known Anuṣṭubh and Triṣṭubh verses are detected correctly.

## Limitations and ideas for improvement

- _Be honest here: for example, handling of conjunct consonants, anusvāra/visarga, or edge cases in meter detection._
- Possible extensions: more meters, Mātrā-based meters, a Prastāra table viewer, and automated tests.

## References

- Pingala, *Chandaḥśāstra* (the source of the Nāṣṭa and Uddiṣṭa rules)
- Halāyudha's commentary (*Mṛtasañjīvanī*) for the commonly quoted formulation

## Author

**Pranjal Patil** — B.Tech AI & Data Science, Modern College of Engineering, Pune
[LinkedIn](https://www.linkedin.com/in/pranjal-patil-3682883b6/) · [GitHub](https://github.com/patilpranjal2431-dev)
