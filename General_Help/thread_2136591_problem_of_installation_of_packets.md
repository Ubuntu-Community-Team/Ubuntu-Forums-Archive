---
title: "problem of installation of packets"
date: 2013-04-18
forum: General Help
---

### Post by mahanew on 2013-04-18
Hi,
I want to install build-essential.To do so, ihave taped this command 
sudo apt-get install  build-essential Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Aucune version du paquet build-essential n'est disponible, mais il existe dans la base
de données. Cela signifie en général que le paquet est manquant, qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source

E: Le paquet « build-essential » n'a pas de version susceptible d'être installée

I don't understand where i.4.3 the problem .I tried to install it from ubuntu packages using the software center (I'm using ubuntu 12.04TLS);But i have also a problem :
dependancy is not satisfied g++(>=4:4.4.3).
PLEASE help me because I need this package to install VoIP packet genrator SIPP.
Thank you so much.

---

### Post by slickymaster on 2013-04-18
Have you tried:```
sudo apt-get -f install
```This will try to correct broken dependencies.
Then run:```
sudo dpkg --configure -a
```and again:```
sudo apt-get -f install
```

---

