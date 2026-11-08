# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A single-file, dependency-free loan payment calculator: `loan-calculator.html` holds all markup, CSS (in `<style>`), and JavaScript (in `<script>`). There is no build step, package manager, linter, or test suite.

## Running

Open `loan-calculator.html` directly in a browser (e.g. `start loan-calculator.html` on Windows). Reload the page after edits.

## How the calculator works

- The `#loan-form` submit handler reads amount, annual rate (%), and term (months), validates them, then renders everything into `#result` via `innerHTML`.
- Monthly payment uses the standard amortization formula `P·r / (1 − (1+r)^−n)` with `r = annualRate / 100 / 12`; a 0% rate is special-cased to `P / n` to avoid division by zero.
- The amortization schedule loop charges interest on the remaining balance each month. In the final month it pays off the exact remaining balance and forces it to 0, so floating-point leftovers never appear — preserve this when changing the loop.
- All currency output goes through the shared `money` `Intl.NumberFormat` (locale-default, 2 decimals); use it for any new monetary values.

## How to work with me
- I'm a beginner. Before running any terminal command, explain in plain language what it does.
- Explain what you changed after each edit, in simple terms.
- Ask me before adding new files or tools I haven't asked for.