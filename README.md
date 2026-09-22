# Retrofit CNC — ProducMill CV30

Retrofit complet d’un centre d’usinage vertical **ProducMill CV30** afin de moderniser sa commande numérique, ses entraînements, sa broche, son magasin d’outils et ses systèmes de sécurité.

> **État du projet :** en cours de développement et de mise au point.  
> Les fichiers présents dans ce dépôt doivent être adaptés et validés sur la machine réelle avant toute utilisation.

---

## Sommaire

- [Présentation](#présentation)
- [Objectifs](#objectifs)
- [Machine d’origine](#machine-dorigine)
- [Architecture retenue](#architecture-retenue)
- [Entraînements des axes](#entraînements-des-axes)
- [Broche](#broche)
- [Capteur du magasin](#capteur-du-magasin)
- [Changeur automatique d’outils](#changeur-automatique-doutils)
- [Sécurité](#sécurité)
- [Organisation du dépôt](#organisation-du-dépôt)
- [Mise en service](#mise-en-service)
- [Validation de la précision](#validation-de-la-précision)
- [État du projet](#état-du-projet)
- [Avertissements](#avertissements)
- [Licence](#licence)

---

## Présentation

La machine concernée est une fraiseuse CNC verticale **ProducMill CV30**, acheter sans CN et table démonté et sans vis ni patins, pour 700€

Le retrofit a pour objectif de conserver autant que possible la mécanique existante tout en remplaçant les éléments électroniques et de commande devenus obsolètes.

Le système est basé sur :

- un Raspberry Pi 4 ;
- LinuxCNC ;
- une carte Mesa 7i96S ;
- des servomoteurs modernes pour les axes ;
- un servomoteur dédié à la broche ;
- un magasin automatique de 12 outils ;
- une architecture de sécurité modernisée.

---

## Objectifs

Les objectifs principaux du projet sont :

- améliorer la précision dimensionnelle ;
- obtenir une répétabilité cible inférieure à `±0,01 mm` ;
- remplacer la commande numérique d’origine ;
- moderniser les variateurs et les moteurs ;
- fiabiliser la commande de broche ;
- conserver et automatiser le magasin d’outils ;
- intégrer l’orientation de broche ;
- préparer l’ajout d’un palpeur ;
- faciliter la maintenance ;
- documenter le câblage et les réglages ;

La précision finale dépendra notamment de l’état mécanique de la machine, des jeux des vis, de la rigidité, du réglage des servomoteurs et de la température.

---

## Machine d’origine

| Élément | Caractéristique |
|---|---|
| Marque et modèle | ProducMill CV30 |
| Type | Centre d’usinage vertical |
| Commande d’origine | NUM 1020 CNC |
| Puissance de broche d’origine | 5,5 kW |
| Course X | 250 mm |
| Course Y | 250 mm |
| Course Z | 300 mm |
| Table | 500 × 250 mm |
| Distance maximale table / nez de broche | 350 mm |
| Cône de broche | ISO 30 / ISO 7388 |
| Tirette | ISO 7388/3 ou M12 D13,35 |
| Magasin | 12 outils |

---

## Architecture retenue

### Commande numérique

- **Ordinateur :** Raspberry Pi 4
- **Logiciel :** LinuxCNC
- **Carte d’interface :** Mesa 7i96S
- **Communication :** Ethernet
- **Adresse IP actuelle :** `10.10.10.10`

La carte Mesa assure notamment :

- la génération des signaux Step/Dir ;
- la lecture des entrées machine ;
- la commande des sorties ;
- la gestion des encodeurs ;
- l’interface avec les capteurs ;
- la commande du magasin automatique.

trivkins coordinates=XYZ
