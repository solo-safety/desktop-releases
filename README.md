# Solo-Safety Desktop — releases

Official Windows releases of **Solo-Safety Desktop**, the desktop client of [solo-safety.com](https://solo-safety.com).

**To install, use the website:** open [solo-safety.com](https://solo-safety.com) and press the *Desktop* button. The site always offers the newest release here, and it checks each file's SHA-256 and signature before it hands the file to you.

This repository holds **only published release files**. It has no source code and nothing in it can be run from the repository itself. The application's source is private.

## What each release contains

| File | What it is |
|---|---|
| `Solo-Safety-Setup-<version>-x64.exe` | the installer (per-user, no administrator rights needed); installed copies update themselves |
| `Solo-Safety-Portable-<version>-x64.exe` | a build that needs no installation and does not update itself |
| `*.exe.sig` | the Ed25519 signature of that file, made in the release pipeline |
| `SHA256SUMS.txt` | SHA-256 of the executables |
| `latest.yml`, `*.blockmap` | metadata the installed application reads to update itself |

## Checking a download by hand

```powershell
Get-FileHash .\Solo-Safety-Setup-<version>-x64.exe -Algorithm SHA256
```

The hash must equal the line for that file in `SHA256SUMS.txt` (and the one the website shows under *تأكد من الملف*).

## About the Windows warning

These builds are **not Authenticode-signed** (there is no code-signing certificate), so on first run Windows SmartScreen may show *"Windows protected your PC"*. Choose *More info*, then *Run anyway*. The publisher is **Solo-Safety**; the checks above are how you confirm the file is the one that was published. On a Windows 11 PC with *Smart App Control* switched on, unsigned programs can be blocked outright.

## Updates

An installed copy checks this repository's releases, downloads a newer version in the background, and **refuses to install it unless its signature verifies** against the public key built into the application. Versions only go up; the application never downgrades.

## Help

Questions go through the Discord server linked on [solo-safety.com](https://solo-safety.com).
