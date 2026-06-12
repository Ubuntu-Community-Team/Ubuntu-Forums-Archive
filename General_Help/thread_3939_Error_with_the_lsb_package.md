---
title: "Error with the lsb package"
date: 2004-11-10
forum: General Help
---

### Post by EcliptuX on 2004-11-10
I have an error when I try to install the lsb package (and is dependencies).
```
root@toto:/var/cache/apt/archives # apt-get install lsb
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Les NOUVEAUX paquets suivants seront installés :
  lsb
0 mis à jour, 1 nouvellement installés, 0 à enlever et 1 non mis à jour.
Il est nécessaire de prendre 0o/28,0ko dans les archives.
Après dépaquetage, 127ko d'espace disque supplémentaires seront utilisés.
Preconfiguring packages ...
(Lecture de la base de données... 82915 fichiers et répertoires déjà installés.)
Dépaquetage de lsb (à partir de .../archives/lsb_2.0-1_i386.deb) ...
dpkg : erreur de traitement de /var/cache/apt/archives/lsb_2.0-1_i386.deb (--unpack) :
 tentative de remplacement de « /lib/lsb/init-functions », qui appartient aussi au paquet lsb-base
dpkg-deb: sous-processus paste tué par le signal (Relais brisé (pipe))
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/lsb_2.0-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@toto:/var/cache/apt/archives #
```I tried to remove lsb and reinstall without succes.
Do you know where is the problem ?

Thx

---

### Post by EcliptuX on 2004-11-10
precision : the error occurs when I try to upgrade lsb-1.3-9ubuntu7(warty) to lsb-2.0-1(unstable)

---

### Post by macro182 on 2007-09-25
Hi!

You've resolved? :)

---

