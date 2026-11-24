# PotablaVAN

Web del blog [potablavan.com](https://potablavan.com): Hugo amb el tema Future Imperfect i una portada pròpia. Es publica a GitHub Pages.

## Tema

`themes/future-imperfect-slim` és un submòdul de git que apunta al nostre fork,
[onavascuez/hugo-future-imperfect-slim](https://github.com/onavascuez/hugo-future-imperfect-slim).
El tema original es va abandonar el 2022; el fork el fa compilar amb Hugo actual.
Els arreglos del tema es fan al fork, no aquí.

Fan falta **Hugo** i **Dart Sass** (el tema compila els seus estils amb Sass): `brew install hugo` i `brew install sass/sass/sass`.

Després de clonar el repo:

```
git submodule update --init
```

## Veure-la en local

```
hugo server -D
```

Obre http://localhost:1313. `-D` ensenya també els esborranys (`draft: true`), que a la web publicada no surten.

## Escriure

- Cada entrada és un fitxer Markdown dins de `content/viatges/`, `content/guies/` o `content/arees-camper/`.
- **Entrada gran de la portada:** la que porti `portada: true` a la capçalera. Per canviar-la, treu-lo d'una i posa'l a l'altra.
- **Destacades del lateral:** les entrades que portin `destacat: true`. En surten tres, les més recents.
- **Foto d'una entrada:** `featured: "nom.jpg"` i `featuredpath: "viatges"` a la capçalera; la foto va a `static/img/viatges/nom.jpg`. Amb `featuredalt` s'hi posa el text alternatiu.
- **Text de cada bloc de la portada:** al fitxer `_index.md` de la secció (`description` i `totes`). La seva foto, igual que la d'una entrada.

## On és cada cosa

| Què | On |
|---|---|
| Portada (entrada gran i tres blocs) | `layouts/home.html` |
| Lateral (destacades, últimes, nosaltres) | opcions `[params.sidebar]` de `hugo.toml`; la plantilla és del tema |
| Estils propis | `static/css/add-on.css` |
| Menú, lateral, lema i seccions | `hugo.toml` |
| Textos del tema que canviem | `i18n/ca.toml` |
| Logo | `static/img/logo-potablavan.png` (original a `assets/img/`) |
| Publicació | `.github/workflows/pages.yml` |

## Publicar

A cada push a `main`, la GitHub Action genera el lloc i el publica. Les versions de Hugo i de Dart Sass estan fixades al workflow: si s'actualitzen en local, cal actualitzar-les allà també.
