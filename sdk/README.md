# 🎬 MovieLens SDK - `sylla_films`

Un SDK Python moderne permettant d’accéder à l’API MovieLens  
déployée sur Render.  
Idéal pour les **Data Analysts**, **Data Scientists**, étudiants, et projets ML.

[![PyPI version](https://img.shields.io/pypi/v/sylla-films.svg)](https://pypi.org/project/sylla-films/)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

---

## 🚀 Installation

```bash
pip install sylla_films
```

---

## ⚙️ Configuration

```python
from sylla_films.film_client import MovieClient
from sylla_films.film_config import MovieConfig

config = MovieConfig(
    movie_base_url="https://projet-api-et-deploiement-2.onrender.com"
)

client = MovieClient(config=config)
```

Ou via une variable d’environnement :

```
MOVIE_API_BASE_URL=https://projet-api-et-deploiement-2.onrender.com
```

Puis :

```python
client = MovieClient()
```

---

## 🩺 Tester le SDK

### 🔍 1. Health Check

```python
client.health_check()
# → {"message": "API MovieLens opérationnelle"}
```

---

## 🎞️ 2. Récupérer un film

```python
movie = client.get_movie(1)
print(movie.title)
```

Résultat :

```
Toy Story (1995)
```

---

## 📋 3. Liste de films dans plusieurs formats

### a) Format Pydantic (par défaut)

```python
movies = client.list_movies(limit=5)
print(movies[0].title)
```

### b) Format dictionnaire

```python
movies_dict = client.list_movies(limit=5, output_format="dict")
```

### c) Format Pandas DataFrame

```python
df = client.list_movies(limit=5, output_format="pandas")
print(df.head())
```

---

## ⭐ Formats supportés

| Format demandé           | Retour |
|-------------------------|--------|
| `"pydantic"` (défaut)  | Liste d’objets Pydantic |
| `"dict"`               | Liste de dictionnaires |
| `"pandas"`             | Pandas DataFrame |

Exemple :

```python
client.list_ratings(limit=10, output_format="pandas")
```

---

## 🧩 Travailler avec les autres endpoints

### 🎭 Rating

```python
rating = client.get_rating(user_id=1, movie_id=1)
print(rating.rating)
```

### 🏷️ Tags

```python
tags = client.list_tags(limit=5, output_format="dict")
```

### 🔗 Liens IMDB / TMDB

```python
link = client.get_link(1)
print(link.imdbId)
```

### 📊 Analytics global

```python
analytics = client.get_analytics()
print(analytics.movie_count)
```

---

## 🧪 Tester avec une API locale

```python
config = MovieConfig(movie_base_url="http://localhost:8000")
client = MovieClient(config=config)
```

---

## 👥 Public cible

- Data Analysts  
- Data Scientists  
- Étudiants  
- Développeurs Python  
- Projets ML / IA  

---

## 📄 Licence

MIT License

---

## 🔗 Liens utiles

- API Render : https://projet-api-et-deploiement-2.onrender.com  
- Documentation interactive : https://projet-api-et-deploiement-2.onrender.com/docs  
- PyPI : https://pypi.org/project/sylla-films/
