---
title: "Bugs with firebird (sql) 2.1 package ?"
date: 2013-01-28
forum: General Help
---

### Post by juju43 on 2013-01-28
I tried to replicate a database from windows on a linux for testing.

I installed firebird2.1-super on my linux (lubuntu 12.04 up to date) but it seems package is broken and can't even uninstalled

```
$ dpkg-reconfigure firebird2.1-super
 * Starting Firebird 2.1 server manager...
terminate called after throwing an instance of 'Firebird::status_exception'
check /var/log/firebird2.1.log file for errors
can not start server
   ...done.

```=> can't start

if try to uninstall (to test w 2.5)
```
$ sudo apt-get remove firebird2.1-super 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Le paquet firebird2.1-super n'est pas installé, et ne peut donc être supprimé
Le paquet suivant a été installé automatiquement et n'est plus nécessaire :
  firebird2.1-common
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets suivants seront ENLEVÉS :
  firebird2.1-server-common
0 mis à jour, 0 nouvellement installés, 1 à enlever et 11 non mis à jour.
1 partiellement installés ou enlevés.
Après cette opération, 1 675 ko d'espace disque seront libérés.
Souhaitez-vous continuer [O/n] ? 
(Lecture de la base de données... 346158 fichiers et répertoires déjà installés.)
Suppression de firebird2.1-server-common ...
rmdir : option non reconnue « --ignore-if-not-empty »
Saisissez « rmdir --help » pour plus d'informations.
dpkg : erreur de traitement de firebird2.1-server-common (--remove) :
 le sous-processus script post-removal installé a retourné une erreur de sortie d'état 1
Aucun rapport « apport » écrit car MaxReports a déjà été atteint
                                                                Des erreurs ont été rencontrées pendant l'exécution :
 firebird2.1-server-common

E: Sub-process /usr/bin/dpkg returned an error code (1)
```reported a bug here
[https://bugs.launchpad.net/ubuntu/+source/firebird2.1/+bug/1108486](https://bugs.launchpad.net/ubuntu/+source/firebird2.1/+bug/1108486)

but want to know if other people encountered the same problem and solved it.

Thanks a lot.
Cheers

---

