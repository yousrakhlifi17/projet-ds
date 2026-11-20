# Projet Data Science - Breast Cancer Wisconsin

Ce projet est realise dans le cadre de l'Atelier 01 consacre a Git et DVC.

Il permet de versionner un jeu de donnees avec DVC et de mettre en place un pipeline reproductible de preparation des donnees.

## Jeu de donnees

Jeu : UCI Breast Cancer Wisconsin (Diagnostic).

- Nombre d'observations : 569
- Nombre de colonnes : 32
- Cible : `diagnosis`
- Encodage : B = 0, M = 1
- Colonne `id` supprimee lors de la preparation.

## Pipeline de preparation

Le stage `prepare` realise les operations suivantes :

- Suppression de la colonne `id`.
- Encodage de la variable cible.
- Separation des donnees en train et test.
- Decoupage stratifie avec `test_size = 0.2` et `seed = 42`.

Les donnees preparees sont enregistrees dans `data/prepared/`.

## Utilisation de DVC

### 1. Configurer le stockage local

```bash
dvc remote add --local -d storage <dossier>
```

### 2. Recuperer les donnees

```bash
dvc pull
```

### 3. Rejouer le pipeline

```bash
dvc repro
```

### 4. Telecharger a nouveau les donnees depuis UCI si necessaire

```bash
python scripts/get_data.py
```

## Verification

```bash
python scripts/check_data.py
python scripts/check_prepared.py
dvc status
```

## Version de reference

Tag Git : `data-bc-v1`

Parametres de reference :
- `test_size = 0.2`
- `seed = 42`

MD5 du dataset original :

`f4aecff5892354dc4c7879d8ee2b3c09`