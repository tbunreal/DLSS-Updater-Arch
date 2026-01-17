# DLSS Updater (Community AppImage for Arch/CachyOS)

> **⚠️ Community Distribution:** This is a community-maintained fork of [Recol/DLSS-Updater](https://github.com/Recol/DLSS-Updater). This fork provides a standalone **AppImage** specifically for Arch Linux and CachyOS users who prefer a native, un-sandboxed portable binary over Flatpak. 
> 
> *For official support or the Flatpak version, please visit the original repository.*

[![CodeQL](https://github.com/Recol/DLSS-Updater/actions/workflows/github-code-scanning/codeql/badge.svg)](https://github.com/Recol/DLSS-Updater/actions?query=workflow%3ACodeQL)
[![CodSpeed](https://img.shields.io/endpoint?url=https://codspeed.io/badge.json)](https://codspeed.io/Recol/DLSS-Updater?utm_source=badge)
![Version](./version.svg)
![Downloads](https://img.shields.io/github/downloads/Recol/DLSS-Updater/total?color=blue&label=Downloads)
[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-donate-yellow.svg)](https://buymeacoffee.com/decouk)

![dlss_updater](https://github.com/user-attachments/assets/b7d7fb4d-e204-412d-8e92-61a7173abfaf)

What if you could update all the DLSS/XeSS/FSR DLLs for the games detected on your system?

## Features

- **Portable AppImage Support:** Works natively on Arch-based systems without installation.
- **Cross-Platform Support:** Works on both Windows and Linux.
- Supports updating games from the following launchers:
  - Steam (including Proton games on Linux)
  - Ubisoft
  - EA Play
  - Xbox Game Pass (PC) - Windows only
  - Epic Games Launcher
  - GOG Galaxy
  - Battle.net (Ensure launcher is **open** before updating).
- **Linux Support:**
  - Scans Steam Proton prefixes for Windows games.
  - Supports Wine prefixes (Lutris, standalone Wine).
  - Automatic Steam path detection on Linux.
  - Custom folder support for any game location.
  - Enable the DLSS Debug Overlay.
- **DLSS SR Preset Override:**
  - Configure DLSS Super Resolution presets (K/L/M) with GPU-based recommendations.
  - Windows: System-wide registry override.
  - Linux: Generate Steam launch options with copy-to-clipboard.
- Built-in backup system for restoring game binaries.
- Support for Ray Reconstruction, Frame Generation, and Streamline (Reflex) DLLs.
- Support for XeSS/FSR/DirectStorage DLLs.

The current supported DLLs include:
- DLSS 4.5 (v3.10.5) / FG & RR (v3.10.5).
- FSR 4 (v4.0.2.0).
- XeSS 2.0.2, XeSS Frame Generation 1.2.2, and XeLL 1.2.1.

## GUI
<img width="1097" height="716" alt="image" src="https://github.com/user-attachments/assets/59732e2c-add3-4ad2-ac85-0e0fed6e7ee9" />

---

## Execution Instructions

### Windows

#### Running the Pre-built Application
1. Download the latest release from the [Original Releases](https://github.com/Recol/DLSS-Updater/releases) page.
2. Extract the `DLSS.Updater.X.Y.Z.zip` file.
3. Run `DLSS_Updater.exe` as administrator.

#### Winget / Chocolatey
`winget install "DLSS Updater"` or find it on [Chocolatey](https://community.chocolatey.org/packages/dlss-updater/).

---

### Linux

#### AppImage (Recommended for Arch/CachyOS)
This version is provided by this fork for users who want a native, portable experience.

1. Download the `.AppImage` from the [Releases](https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME/releases) page.
2. Make it executable:
   ```bash
   chmod +x DLSS_Updater-x86_64.AppImage
   ```
3. Run it:
   ```bash
   ./DLSS_Updater-x86_64.AppImage
   ```

#### Flatpak (Official Method)
```bash
# Arch
sudo pacman -S flatpak
flatpak remote-add --if-not-exists flathub [https://dl.flathub.org/repo/flathub.flatpakrepo](https://dl.flathub.org/repo/flathub.flatpakrepo)
flatpak install flathub io.github.recol.dlss-updater
flatpak run io.github.recol.dlss-updater
```

---

## Building from Source

### Prerequisites
- Python 3.14+ (free-threaded recommended)
- Git
- `uv` (Python package manager)

### Building the AppImage (Linux)
To reproduce the AppImage provided in this repository:

1. **Clone the fork:**
   ```bash
   git clone [https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME.git)
   cd DLSS-Updater
   ```
2. **Install Dependencies:**
   ```bash
   uv sync --frozen
   ```
3. **Build Binary:**
   ```bash
   uv run pyinstaller DLSS_Updater_Linux.spec
   ```
4. **Package:**
   Place the binary into an `AppDir` with the `.desktop` file and icon, then run:
   ```bash
   ARCH=x86_64 ./appimagetool-x86_64.AppImage AppDir
   ```

---

## Blacklisted Games
The blacklist is maintained in a [separate repository](https://github.com/Recol/DLSS-Updater-Whitelist/blob/main/whitelist.csv). It includes games that use custom testing versions, replace DLLs on boot (Warframe), or use non-updatable DLSS <2.0.

## Troubleshooting
If you receive a `libmpv` issue, your distro may not be bundling the library. See [Issue #125](https://github.com/Recol/DLSS-Updater/issues/125) for guidance.

## License
This project is licensed under the **GNU Affero General Public License v3.0**. See the `LICENSE` file for details. This fork adheres to AGPL-3.0 by providing the corresponding source code for the AppImage distribution.

## Credits
Original code by **Recol**. This project uses Nvidia's DLSS and Intel's XeSS technologies. Special thanks to the contributors of `pefile`, `psutil`, `Pyinstaller`, and `flet`.
