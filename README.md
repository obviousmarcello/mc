# Modern Ceremoniamester

GitHub Pages-kompatibilis, teljesen statikus weboldal egy modern ceremóniamester és esküvői weboldal szolgáltatás számára.

## Mi változott

A projekt most már backend nélkül, tiszta HTML/CSS/JavaScript alapon működik:

- `index.html`: a teljes oldal markupja
- `styles.css`: a vizuális rendszer és reszponzív layout
- `app.js`: a kétnyelvű tartalom, renderelés és a kapcsolatfelvételi logika
- `images/`: az Instagram alapján használt képi anyag

Ez a struktúra közvetlenül publikálható GitHub Pages-en a repository gyökeréből.

## GitHub Pages

1. Töltsd fel a repository-t GitHubra.
2. A repo `Settings > Pages` részén állítsd a `Source` értékét `GitHub Actions`-re.
3. Pusholj a `main` vagy `master` branch-re.

Az oldal ezután a workflow-n keresztül fog automatikusan publikálódni, nincs szükség külön szerverre.

## Automatikus deploy GitHub Actions-szel

Hozzáadtam egy Pages workflow-t ide:

```text
.github/workflows/deploy-pages.yml
```

Mit csinál:

- minden `main` vagy `master` branch push után lefut
- összecsomagolja a statikus fájlokat
- publikálja őket GitHub Pages-re

Fontos:

- a GitHub repository `Settings > Pages` részén a `Source` legyen `GitHub Actions`
- mivel ez a workspace jelenleg nem git repository, a tényleges `git init`, `remote add`, `commit` és `push` lépéseket a GitHub repódban kell megtenni

Ha a repository már GitHubon van, elég feltölteni ezeket a fájlokat és a workflow automatikusan deployolni fog.

## Kétnyelvűség

Beépítettem egy `HU / EN` váltót:

- a teljes fő tartalom nyelvet vált
- a form címkék és placeholder szövegek is váltanak
- a választott nyelv `localStorage`-ban mentődik

## Kapcsolatfelvétel backend nélkül

GitHub Pages-en nincs saját szerveroldali `POST` feldolgozás, ezért az ajánlatkérő űrlap most így működik:

- előre kitölt egy `mailto:` e-mailt
- a beküldött üzenetet a vágólapra is másolja

Ez GitHub Pages-kompatibilis, de ha később valódi űrlapbeküldést szeretnél, külső szolgáltatót vagy külön backend-et kell mögé tenni.

## Lokális előnézet

Mivel statikus oldalról van szó, akár a fájlt közvetlenül is megnyithatod böngészőben, de egy egyszerű helyi szerverrel megbízhatóbb:

```bash
python3 -m http.server 8000
```

Utána:

```text
http://127.0.0.1:8000
```
