<p align="center">
  <a href="https://sp-night.github.io">
    <img src="https://raw.githubusercontent.com/sp-night/sp-night.github.io/main/public/logo-noite.svg" width="120" alt="SP Night — the Pico do Jaraguá at dusk, aviation beacon lit, the city's lights at the foot of the range">
  </a>
</p>

<h1 align="center">SP Night for <a href="https://eza.rocks/">eza</a></h1>

<p align="center">
  <strong>The sodium lamp turns the whole city this colour.</strong><br>
  A dark colour scheme with São Paulo as its reference — the sodium street lamp,<br>
  exposed concrete, the free span of the MASP, the drizzle before the rain.
</p>

<p align="center">
  <a href="https://sp-night.github.io"><strong>sp-night.github.io</strong></a>
  &nbsp;·&nbsp;
  <a href="https://sp-night.github.io/palette">palette</a>
  &nbsp;·&nbsp;
  <a href="https://sp-night.github.io/spec">spec</a>
  &nbsp;·&nbsp;
  <a href="https://sp-night.github.io/ports">ports</a>
</p>

---

## The flavours

All three are dark, by decision. The previews below are synthetic — drawn from the
palette itself, so they can never drift from what you install.

### Noite Paulista — `sp_night_noite.sh`

The city at 3am. Blue-violet dark, the sodium lamp burning warm on top.

![eza themed with SP Night Noite Paulista](assets/preview-noite.svg)

### Garoa — `sp_night_garoa.sh`

The same window, seen through the drizzle. Flat grey — the garoa does not cool
the city down, it washes it out.

![eza themed with SP Night Garoa](assets/preview-garoa.svg)

### Pico do Jaraguá — `sp_night_jaragua.sh`

The same night, seen from the city's highest point. The dark rotated towards the
green of the forest, the red-and-white tower lit at the top.

![eza themed with SP Night Pico do Jaraguá](assets/preview-jaragua.svg)

## Install

eza reads its colours from the `EZA_COLORS` environment variable — each theme is
a small shell file that exports it, meant to be sourced from your shell rc.

Grab the flavour you want (or all three):

```sh
mkdir -p ~/.config/eza
curl -Lo ~/.config/eza/sp_night_noite.sh \
  https://raw.githubusercontent.com/sp-night/eza/main/themes/sp_night_noite.sh
```

Then source it from `~/.bashrc` or `~/.zshrc`:

```sh
source ~/.config/eza/sp_night_noite.sh
```

On fish, translate the export in `~/.config/fish/config.fish`:

```fish
set -gx EZA_COLORS (bash -c 'source ~/.config/eza/sp_night_noite.sh && printf %s "$EZA_COLORS"')
```

Open a new shell (or re-source the rc) and every `eza` invocation picks it up.

Prefer a checkout? Clone and copy — the files are plain text, there is no build:

```sh
git clone https://github.com/sp-night/eza.git
cp eza/themes/* ~/.config/eza/
```

## What gets themed

| eza key | Role | Meaning |
|---|---|---|
| `di` | `syntax.keyword` | directories in bold *marginal* — the expressway sign pointing the way |
| `ex` | `diagnostic.ok` | executables in bold *ibira*, green light |
| `ln` / `lp` | `syntax.operator` / `syntax.function` | symlinks and their targets in *sereno*, the cold signage of dawn |
| `ur` `uw` `ux` (+ group/other) | `syntax.constant` / `diagnostic.error` / `diagnostic.ok` | read is *sódio*, write is *brasa*, execute is *ibira* |
| `sn` / `sb` | `syntax.number` / `ui.fg_dim` | file sizes — the number burns, the unit recedes |
| `uu` / `un` | `ui.fg_dim` / `ui.fg_muted` | your user quiet, everyone else quieter |
| `da` | `ui.fg_muted` | dates as ornament, never shouting |
| `ga` `gm` `gd` | `git.added` / `git.modified` / `git.removed` | git status in *ibira* / *táxi* / *brasa* |
| `pi` `so` `bd` `cd` | `syntax.type` / `syntax.macro` / `syntax.attribute` | pipes, sockets and devices in *temporal*, *estaiada*, *táxi* |
| `*.go`, `*.rs`, `*.py`, … | per-language accents | source files keep the same accents the editor port gives them |

No hex in this repo was picked by hand: every value is generated from the
[SP Night palette](https://sp-night.github.io/palette) through its semantic role
layer, and the palette itself passes a contrast audit —
[every rule in the spec is a CI gate, not a promise](https://sp-night.github.io/spec).

## License

[MIT](LICENSE)
