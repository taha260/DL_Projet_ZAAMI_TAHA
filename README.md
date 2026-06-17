# Projet Deep Learning — MusicAI

## Description du projet

Ce projet a été réalisé dans le cadre du module **Deep Learning**.  
L’objectif principal est de comparer plusieurs familles de modèles de Deep Learning selon la nature des données étudiées :

- **MLP** pour les données tabulaires ;
- **CNN** pour les images ou spectrogrammes ;
- **RNN / LSTM / GRU / Seq2Seq** pour les données séquentielles.

Le fil conducteur du projet est l’analyse musicale. Les modèles sont appliqués à différents types de représentations de la musique : caractéristiques audio tabulaires, spectrogrammes et séquences MIDI.

---

## Structure du dépôt GitHub

Le dépôt contient les fichiers suivants :

```text
.
├── Figures_MusicAI.zip
├── Partie_1_MLP_Spotify.ipynb
├── Partie_2_CNN_GTZAN.ipynb
├── Partie_3_RNN_MAESTRO.ipynb
└── Rapport_Deep_Learning.pdf
```

### Description des fichiers

| Fichier | Description |
|---|---|
| `Partie_1_MLP_Spotify.ipynb` | Notebook de la Partie I : classification supervisée sur données tabulaires avec un MLP appliqué au dataset Spotify Tracks. |
| `Partie_2_CNN_GTZAN.ipynb` | Notebook de la Partie II : classification de genres musicaux avec CNN à partir de spectrogrammes du dataset GTZAN. |
| `Partie_3_RNN_MAESTRO.ipynb` | Notebook de la Partie III : modélisation et génération de séquences musicales avec RNN, LSTM, GRU et Seq2Seq sur le dataset MAESTRO MIDI. |
| `Figures_MusicAI.zip` | Archive contenant les figures utilisées dans le rapport : courbes d’entraînement, matrices de confusion, visualisations de spectrogrammes et cartes de caractéristiques. |
| `Rapport_Deep_Learning.pdf` | Rapport final du projet au format PDF. |

---

## Partie I — MLP sur données tabulaires Spotify

La première partie porte sur la classification musicale à partir de caractéristiques audio tabulaires.

### Objectifs

- Charger et préparer le dataset Spotify Tracks.
- Nettoyer les données et sélectionner les variables numériques pertinentes.
- Encoder les genres musicaux.
- Normaliser les caractéristiques avec `StandardScaler`.
- Implémenter deux versions du MLP :
  - une version avec `nn.Sequential` ;
  - une version avec une classe personnalisée héritant de `nn.Module`.
- Tester plusieurs stratégies d’initialisation :
  - gaussienne ;
  - constante ;
  - Xavier.
- Évaluer les modèles avec :
  - accuracy ;
  - précision ;
  - rappel ;
  - F1-score ;
  - matrice de confusion.

### Dataset utilisé

Le dataset utilisé est **Spotify Tracks Dataset**.  
Il contient des caractéristiques audio comme :

- `danceability`
- `energy`
- `loudness`
- `speechiness`
- `acousticness`
- `instrumentalness`
- `liveness`
- `valence`
- `tempo`
- `popularity`
- `duration_ms`

---

## Partie II — CNN sur spectrogrammes GTZAN

La deuxième partie porte sur la classification d’images musicales sous forme de spectrogrammes.

### Objectifs

- Charger les fichiers audio du dataset GTZAN.
- Transformer les fichiers audio en spectrogrammes Mel.
- Implémenter manuellement :
  - la corrélation croisée 2D ;
  - le max-pooling ;
  - l’average-pooling.
- Comparer les implémentations manuelles avec les couches PyTorch.
- Implémenter un CNN inspiré de LeNet.
- Comparer un MLP appliqué aux spectrogrammes aplatis avec un CNN.
- Étudier l’influence de plusieurs choix architecturaux :
  - padding ;
  - stride ;
  - pooling ;
  - nombre de filtres ;
  - convolution `1 × 1`.
- Visualiser les cartes de caractéristiques apprises par le CNN.

### Dataset utilisé

Le dataset utilisé est **GTZAN Music Genre Classification**.  
Il contient 10 genres musicaux :

- blues
- classical
- country
- disco
- hiphop
- jazz
- metal
- pop
- reggae
- rock

---

## Partie III — RNN, LSTM, GRU et Seq2Seq sur MAESTRO

La troisième partie porte sur la modélisation de séquences musicales à partir de fichiers MIDI.

### Objectifs

- Charger les fichiers MIDI du dataset MAESTRO.
- Extraire les notes MIDI sous forme de séquences.
- Créer un vocabulaire de notes.
- Préparer une tâche de prédiction de la prochaine note.
- Implémenter et comparer :
  - RNN simple ;
  - LSTM ;
  - GRU.
- Utiliser le gradient clipping pour stabiliser l’entraînement.
- Calculer la perplexité.
- Implémenter un mini système Seq2Seq encodeur-décodeur.
- Tester :
  - greedy decoding ;
  - beam search.
- Générer des séquences musicales simples.

### Dataset utilisé

Le dataset utilisé est **MAESTRO MIDI-only**.  
Seule la version MIDI est utilisée afin d’éviter le téléchargement de la version audio complète, beaucoup plus volumineuse.

---

## Environnement utilisé

Le projet a été développé et exécuté sur **Google Colab**.

### Bibliothèques principales

- Python
- PyTorch
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- Librosa
- PrettyMIDI / Mido

---

## Exécution des notebooks

Les notebooks doivent être exécutés dans l’ordre suivant :

1. `Partie_1_MLP_Spotify.ipynb`
2. `Partie_2_CNN_GTZAN.ipynb`
3. `Partie_3_RNN_MAESTRO.ipynb`

Chaque notebook est indépendant et contient sa propre configuration.

### Étapes générales

1. Ouvrir le notebook dans Google Colab.
2. Monter Google Drive si nécessaire.
3. Vérifier que les datasets sont bien placés dans le dossier du projet.
4. Activer le GPU si disponible :

```text
Exécution > Modifier le type d’exécution > Accélérateur matériel > GPU
```

5. Exécuter les cellules dans l’ordre.

---

## Organisation attendue des datasets dans Google Drive

Les datasets ne sont pas inclus directement dans ce dépôt GitHub à cause de leur taille.  
Ils doivent être placés dans Google Drive avec la structure suivante :

```text
Projet_Deep_Learning_Musique/
├── data/
│   ├── spotify/
│   │   └── spotify_tracks.csv
│   ├── gtzan/
│   │   └── genres_original/
│   └── maestro/
│       └── maestro-v3.0.0/
├── models/
└── results/
```

---

## Résultats attendus

Le projet produit plusieurs types de résultats :

- tableaux comparatifs des modèles ;
- courbes d’entraînement ;
- matrices de confusion ;
- rapports de classification ;
- visualisations de spectrogrammes ;
- cartes de caractéristiques CNN ;
- exemples de séquences musicales générées.

Les figures importantes sont regroupées dans :

```text
Figures_MusicAI.zip
```

---

## Rapport

Le fichier `Rapport_Deep_Learning.pdf` contient :

- une introduction générale ;
- une étude théorique de chaque famille de modèles ;
- une description des datasets ;
- les résultats expérimentaux ;
- une analyse critique ;
- une comparaison globale entre MLP, CNN et modèles séquentiels ;
- une conclusion générale.

---

## Auteur

**Taha ZAAMI**  
Filière : Ingénierie Informatique et Réseaux  
Option : Intelligence Artificielle et Data Science  
Module : Deep Learning  
Année universitaire : 2025–2026

---

## Remarque

Les résultats peuvent légèrement varier selon :

- la disponibilité du GPU sur Google Colab ;
- le découpage aléatoire des données ;
- le nombre d’epochs ;
- le mode rapide ou complet utilisé dans les notebooks ;
- la version des bibliothèques installées.
