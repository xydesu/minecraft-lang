# minecraft-lang

A repository that automatically mirrors all Minecraft language (localization) JSON files, keeping them up to date with the latest official releases.

## Current Versions

| Branch | Version |
|--------|---------|
| `main` (stable release) | <!-- LATEST_RELEASE -->26.1.2<!-- /LATEST_RELEASE --> |
| `snapshot` | <!-- LATEST_SNAPSHOT -->26.2-pre-2<!-- /LATEST_SNAPSHOT --> |

## What's in this repo?

- **Language files** – Every `.json` locale file shipped with Minecraft (e.g. `en_us.json`, `zh_tw.json`, `ja_jp.json`, …). Each file is a flat key-value mapping of translation keys to their localized strings.
- **`main` branch** – Tracks the latest **stable release** of Minecraft.
- **`snapshot` branch** – Tracks the latest **snapshot/pre-release** of Minecraft.

## How it works

A GitHub Actions workflow (`fetch-mc-lang.yml`) runs automatically every day at **14:30 UTC**. It:

1. Queries the [Mojang version manifest](https://piston-meta.mojang.com/mc/game/version_manifest_v2.json) for the latest release (and snapshot).
2. Downloads the asset index for that version.
3. Fetches every `minecraft/lang/*.json` file from Mojang's CDN.
4. Extracts `en_us.json` directly from the client JAR (it is not part of the asset index).
5. Commits any changed files back to the appropriate branch.

The workflow can also be triggered manually at any time via the **workflow_dispatch** event.

## Usage

You can use these files directly in your projects to access Minecraft's official translation strings without bundling the game client.

```bash
# Clone the stable release language files
git clone https://github.com/xydesu/minecraft-lang.git

# Or clone the snapshot branch
git clone -b snapshot https://github.com/xydesu/minecraft-lang.git
```

## Language coverage

The repository contains all languages officially supported by Minecraft, including but not limited to:

| Code | Language |
|------|----------|
| `en_us` | English (US) |
| `zh_cn` | Chinese Simplified |
| `zh_tw` | Chinese Traditional |
| `zh_hk` | Chinese (Hong Kong) |
| `ja_jp` | Japanese |
| `ko_kr` | Korean |
| `fr_fr` | French |
| `de_de` | German |
| `es_es` | Spanish (Spain) |
| `pt_br` | Portuguese (Brazil) |
| `ru_ru` | Russian |
| … | and many more |

## License

Language file contents belong to Mojang Studios / Microsoft. This repository redistributes them for convenience. Please refer to [Minecraft's EULA](https://www.minecraft.net/en-us/eula) for usage terms.
