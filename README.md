<div align="center">

<img src="icon.png" alt="ManaVortex" width="120">

# ManaVortex — AltStore Source

**Commander game tracker for Magic: The Gathering**

[![Latest release](https://img.shields.io/github/v/release/schaetzlein/ManaVortex-AltStore?label=latest&color=FF5252)](https://github.com/schaetzlein/ManaVortex-AltStore/releases/latest)
[![iOS 15.5+](https://img.shields.io/badge/iOS-15.5%2B-black)](#requirements)

</div>

This repository is the **iOS distribution channel** for ManaVortex — the AltStore
source catalogue and the signed-on-your-device IPA builds. It holds no
application code; it exists so AltStore has something to point at.

> [!IMPORTANT]
> **This source needs AltStore *Classic* (or SideStore) — not AltStore PAL.**
>
> If you are in the EU, altstore.io leads with **AltStore PAL**, because it is
> the one that installs straight from the browser with no computer. PAL is
> Apple's sanctioned EU marketplace, so it only installs apps that Apple has
> **notarized**. Adding this source to PAL fails with:
>
> > *One or more apps in source "ManaVortex" are missing a marketplaceID. This
> > most likely means they are not notarized, which is not supported by this
> > version of AltStore.*
>
> That is expected, and not something this repository can fix — notarized
> distribution requires an Apple Developer Program membership, EU trader
> verification and Apple's Core Technology Fee per install. Use **AltStore
> Classic** (installed from a computer, see [First-time setup](#first-time-setup))
> or **[SideStore](https://sidestore.io)** instead. Both can sit alongside PAL
> on the same phone.

---

## Add the source

Tap this on the iPhone that has AltStore installed:

**[➕ Add to AltStore](altstore://source?url=https://raw.githubusercontent.com/schaetzlein/ManaVortex-AltStore/main/source.json)**  ·  **[➕ Add to SideStore](sidestore://source?url=https://raw.githubusercontent.com/schaetzlein/ManaVortex-AltStore/main/source.json)**

If your browser does not hand the link off to the app, add it by hand instead —
**AltStore → Browse → Sources → +** — and paste:

```
https://raw.githubusercontent.com/schaetzlein/ManaVortex-AltStore/main/source.json
```

Then open the ManaVortex source and tap **Install**.

## First-time setup

If AltStore is not on the phone yet, that comes first, and it needs a computer:

1. **On the PC or Mac** — install [AltServer](https://altstore.io). This is what
   installs AltStore **Classic**; the browser-based install offered in the EU
   gives you PAL instead, which cannot use this source.
   On Windows it also needs **iTunes and iCloud downloaded from apple.com**, not
   the Microsoft Store versions; the Store builds are sandboxed and do not
   expose the Apple device drivers AltServer links against. This is the usual
   reason a Windows install fails.
2. Connect the iPhone by USB and tap **Trust** on the phone.
3. AltServer tray/menu-bar icon → **Install AltStore** → pick the device → sign
   in with an Apple ID. A free account is fine.
4. **On the iPhone** — Settings → General → VPN & Device Management → trust the
   developer certificate. AltStore will not launch until you do.
5. Add the source above and install ManaVortex.

## Requirements

| | |
|---|---|
| **Installer** | AltStore **Classic** or **SideStore**. AltStore **PAL** cannot use this source — see the note at the top |
| **iOS** | 15.5 or newer |
| **Apple ID** | Any, including a free one — no Apple Developer Program membership |
| **Computer** | Needed once to install AltStore, and again to refresh (see below) |
| **App slots** | A free Apple ID allows **3** sideloaded apps at a time; AltStore itself uses one |

## Keeping it installed

Apps sideloaded with a free Apple ID are signed for **7 days** and stop opening
after that. Refreshing re-signs them — nothing is lost, no data is touched.

- **Automatically** — keep AltServer running on the same Wi-Fi as the phone, and
  enable *Sync with this iPhone over Wi-Fi* in iTunes/Finder. AltStore refreshes
  in the background.
- **By hand** — open AltStore and tap **Refresh All** while AltServer is
  reachable, or reconnect the cable.

If the 7-day cycle grates, [SideStore](https://sidestore.io) refreshes on the
device itself after a one-time pairing, and reads this same source.

## Installing without AltStore

Every release also attaches the plain `ManaVortex.ipa`. Grab it from
[Releases](https://github.com/schaetzlein/ManaVortex-AltStore/releases) and
sideload it with whatever you prefer — Sideloadly, TrollStore on a supported
device, or a paid developer account and Xcode. The IPA is **unsigned**; it is
signed at install time with your own credentials.

## What is in this repository

| File | Purpose |
|---|---|
| `source.json` | The AltStore source catalogue — app metadata and every published version |
| `icon.png` | App and source icon |
| Releases | One tagged GitHub release per version, each with `ManaVortex.ipa` attached |

`source.json` follows the AltStore Source API v2 format (the `apps[].versions[]`
array), which AltStore 2.0+ and SideStore both read. Newest version first; older
entries stay so AltStore can offer a downgrade.

## How a release gets here

Nothing in this repository is edited by hand. The **AltStore Release** workflow
in the ManaVortex build repository runs on demand and does all of it: builds the
unsigned IPA, cuts the tagged release here with the IPA attached, and prepends
the new entry to `source.json` — replacing any existing entry for the same
version rather than stacking a duplicate.

## About the app

ManaVortex tracks Magic: The Gathering **Commander** games at the table — life
totals, commander damage, poison, turn timer, automatic elimination,
a full undoable game log, and post-game statistics. It is **local-first**: your
games live on your device, tracking works with no connection and no account,
and nothing is sent anywhere unless you turn it on. (The card scanner is the
one part that needs a connection — it looks printings up online.)

Signing in with a [ManaVortex-Web](https://magic.sovra.cc) account is optional
and adds two things: your web decks appear in the player slots, and — as a
separate opt-in, off by default — finished games can be published to your
account so the website can show win rates and matchups. The camera permission is
used only by the on-device card scanner.

Available in English, German, French and Spanish.

## Problems?

Open an [issue](https://github.com/schaetzlein/ManaVortex-AltStore/issues).
Installation trouble that turns out to be AltStore itself rather than this app
is usually answered faster at [altstore.io](https://altstore.io).
