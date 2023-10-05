# kodin-ranking
# **Ranking Services**

Le traitement des CV pour trouver un candidat approprié est une tâche difficile pour de nombreuses organisations. La plupart du temps, l’identification des candidats potentiels pour un poste est une tâche longue et coûteuse pour les divisions RH. Les différents CV contiennent des informations dans de nombreux formats. Cette étude extrait les informations du CV et classe les CV selon un critère donné pour éliminer les candidatures inintéressantes reçues dans une organisation. Cette solution de recherche peut nous aider à recommander également la catégorie d’emploi la plus appropriée pour un candidat en fonction des informations de son CV. Ce service peut classer les CV en fonction de divers aspects présentés dans le CV, ce qui permet d’économiser une quantité énorme de temps et d’efforts qui sont nécessaires pour l’analyse manuelle par les recruteurs.

L’architecture du système se compose de deux modules : 
A. Module entreprise Cliente

B. Module de classement des CV

Module entreprise Client se compose de :

## L’entreprise cliente:

Il s’agit de l’entreprise cliente qui nous fournira le descriptif du poste : C.V. avec les exigences et contraintes spécifiques selon lesquelles ils doivent être classés.

Base de données des CV : Il s’agit de la grande base de données qui est utilisée pour stocker la masse des CV fournis par l’entreprise cliente dans un environnement distribué.

Profil social: Les profils sociaux comprennent le profil LinkedIn du candidat, le profil Github du candidat.

Ce module de profil social peut également être étendu à d’autres communautés.

##  Module de classement des CVs

Il composé de :

Système d’analyse syntaxique.

Base de données des compétences des candidats.

Matching des CV.

Système d’analyse syntaxique :

Le système d’analyse syntaxique comprend l’analyse syntaxique des CV des candidats et de leurs profils sociaux en utilisant le langage naturel sans aucune interaction manuelle.C’est ainsi que nous allons analyser les CV un par un.

Bases de données :

Resume.json :

{ “basics”: {

"name": "John Doe",
"label": "Programmer",
"image": "",
"email": "john@gmail.com",
"phone": "(912) 555-4321",
"url": "https://johndoe.com",
"summary": "A summary of John Doe…",
"location": {
  "address": "2712 Broadway St",
  "postalCode": "CA 94115",
  "city": "San Francisco",
  "countryCode": "US",
  "region": "California"
},
"profiles": [{
  "network": "Twitter",
  "username": "john",
  "url": "https://twitter.com/john"
}]
}, “work”: [{

"name": "Company",
"position": "President",
"url": "https://company.com",
"startDate": "2013-01-01",
"endDate": "2014-01-01",
"summary": "Description…",
"highlights": [
  "Started the company"
]
}], “education”: [{

"institution": "University",
"url": "https://institution.com/",
"area": "Software Development",
"studyType": "Bachelor",
"startDate": "2011-01-01",
"endDate": "2013-01-01",
"score": "4.0",
"courses": [
  "DB1101 - Basic SQL"
]
}], “certificates”: [{

"name": "Certificate",
"date": "2021-11-07",
"issuer": "Company",
"url": "https://certificate.com"
}], “skills”: [{

"name": "Web Development",
"level": "Master",
"keywords": [
  "HTML",
  "CSS",
  "JavaScript"
]
}], “languages”: [{

"language": "English",
"fluency": "Native speaker"
}], “interests”: [{

"name": "Wildlife",
"keywords": [
  "Ferrets",
  "Unicorns"
]
}], “projects”: [{

"name": "Project",
"description": "Description…",
"highlights": [
  "Won award at AIHacks 2016"
],
"keywords": [
  "HTML"
],
"startDate": "2019-01-01",
"endDate": "2021-01-01",
"url": "https://project.com/",
"roles": [
  "Team Lead"
],
}

### Réfèrentiel de skills : 
“skills”: [{ “Back”: “Python, R, Matlab, Javascript”, “Font”: “Html, CSS, .NET, DJANGO “, “Microservice”: “Spring boot”, “Data Engineering”: “MongoDB, SQL,POSTGRESQL”, “Paradigme”: “POO” ], }

###### Etape I : CV parsing :
Nous visons dans cette partie de convertir le CV en contenu textuel structuré. Pour atteindre ce but , nous avons utilisé la bibliothèque de parsing pyresparser . Ceci nous permet d’extraire des informations tels que Nom et Prénom , e-mail du candidat , la liste des compétences . On doit comparer la liste des compétences au référentiel des compétences qu’on a déjà .
###### Etape 2 : Similarité entre compétences et compétences de réfèrence : 
Dans cette partie , j’ai utilisé le transformeur multilingue GPT et multilingual bert . J’ai opté pour multilingual bert qui nous a assuré un modèle avec les meilleurs métriques telles que la précision.

