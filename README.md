# Password Strength Checker

A browser-based tool that evaluates password strength in real time — with live scoring, an estimated crack time, and a breach-database lookup powered by [Have I Been Pwned](https://haveibeenpwned.com/).

![Status](https://img.shields.io/badge/status-active-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue)

## Features

- **Live strength meter** — scores your password as you type based on length, character variety, and common patterns
- **Checklist feedback** — instantly shows which requirements are met (length, uppercase/lowercase, numbers, symbols, no repeats/sequences, not a common password)
- **Estimated crack time** — calculates how long an offline brute-force attack would take based on character pool size and password length
- **Breach database check** — checks your password against 800+ million real leaked passwords via the Have I Been Pwned API, using the **k-anonymity model** (see below)
- **Zero data collection** — all strength checks run entirely in your browser; nothing is stored, logged, or sent anywhere except the anonymized breach check

## How the breach check protects your password

This project uses the [Pwned Passwords k-anonymity model](https://haveibeenpwned.com/API/v3#PwnedPasswords):

1. Your password is hashed locally (SHA-1) using the browser's built-in Web Crypto API
2. Only the **first 5 characters** of that hash are sent to the API
3. The API returns all hash suffixes that share that prefix (typically hundreds of matches)
4. The full comparison happens locally in your browser

Your actual password — and even its full hash — **never leaves your device**.

## Running it locally

No installation or server required.

1. Clone this repo:
   ```bash
   git clone https://github.com/simionthespark/password-strength-checker.git
   ```
2. Open `index.html` in any modern browser (double-click it, or right-click → Open with)

That's it — the strength checks work fully offline, and the breach check will work as long as you have an internet connection.

## Tech stack

- **HTML/CSS** — structure and styling, no frameworks
- **Vanilla JavaScript** — all scoring logic and the Web Crypto API for local hashing
- **Have I Been Pwned API** — for breach database lookups

## Why this project

Built as a hands-on way to explore practical password security concepts — entropy estimation, common attack patterns, and privacy-preserving API design (k-anonymity) — while also practicing front-end development.

## Disclaimer

This tool is for educational purposes. It provides a general estimate of password strength and should not be treated as a definitive security guarantee. Always use a reputable password manager to generate and store strong, unique passwords.

## License

MIT — see [LICENSE](LICENSE) for details.
