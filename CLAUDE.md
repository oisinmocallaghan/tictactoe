# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the Game

Open `tictactoe.html` directly in any browser — no build step, server, or dependencies required.

## Architecture

The entire project is a single self-contained file (`tictactoe.html`) with three sections:

- **CSS** (`<style>`): Dark-themed UI using a navy/red/teal palette (`#1a1a2e`, `#e94560`, `#a8dadc`). Layout is CSS Grid for the 3×3 board.
- **HTML**: Static board of 9 `.cell` divs with `data-i` attributes (0–8) used as indices into the game state array.
- **JavaScript** (`<script>`): Vanilla JS with no frameworks. Key state:
  - `board` — 9-element array of `''`, `'X'`, or `'O'`
  - `current` — whose turn it is (`'X'` or `'O'`)
  - `over` — boolean flag preventing clicks after game ends
  - `scores` — `{ X, O, D }` persisted across rounds (reset only on page reload)
  - `WINS` — hardcoded array of the 8 winning index triplets

Game flow: click → update `board[]` → `checkWin()` → highlight winning cells or detect draw → update scores → `init()` on "New Game".

## Git Workflow

- After every code change, commit with a descriptive message and push to GitHub: `https://github.com/oisinmocallaghan/tictactoe`
- This allows easy rollback via git history
