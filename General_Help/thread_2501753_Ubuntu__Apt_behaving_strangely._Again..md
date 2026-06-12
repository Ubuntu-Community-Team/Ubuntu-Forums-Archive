---
title: "Ubuntu : Apt behaving strangely. Again."
date: 2024-10-19
forum: General Help
---

### Post by georgesgiralt on 2024-10-19
Hello Guys,
I own a bunch of computer running Noble after upgrade from the 22.04.5 LTS version. 
I'm seeing a strange behaviour from apt upgrade. 

Often, update are held back due to phasing.  The problem is that the one held back on one computer are installed on another and some are installed and some held back on a third one... 
Example : 
Computer One : ```
apt upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Calcul de la mise à jour... Fait
The following upgrades have been deferred due to phasing:
  gnome-initial-setup libcephfs2 librados2 librbd1
0 mis à jour, 0 nouvellement installés, 0 à enlever et 4 non mis à jour.
```


Computer number Two : ```
apt upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Calcul de la mise à jour... Fait
The following upgrades have been deferred due to phasing:
  libcephfs2 librados2
Les paquets suivants seront mis à jour*:
  gnome-initial-setup
1 mis à jour, 0 nouvellement installés, 0 à enlever et 2 non mis à jour.
Il est nécessaire de prendre 603 ko dans les archives.
Après cette opération, 4&#8239;096 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer*? [O/n]  
```
On this one a previous upgrade installed librbd1 .... And a few hours later I've got the above message. 
Computer Three : ```
apt upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Calcul de la mise à jour... Fait
S'han ajornat les actualitzacions següents degut a escalonament:
  gnome-initial-setup
0 mis à jour, 0 nouvellement installés, 0 à enlever et 1 non mis à jour.
```
This one installed all the libs in a previous upgrade... 

I know I can force the upgrade, but I would like to know what is wrong and how to have apt behave the same on these 3 computers... 

Many thanks in advance for your help and enjoy your week end !

---

### Post by davetheoldcoder on 2024-10-19
This explains that behavior:

> Phased updates depend on a value derived from your machine&#8217;s &#8220;Machine ID&#8221;, as well as the package name and package version.

[https://documentation.ubuntu.com/server/explanation/software/about-apt-upgrade-and-phased-updates/?_ga=2.188709921.821663753.1729358776-767678726.1724008001#how-does-it-actually-work](https://documentation.ubuntu.com/server/explanation/software/about-apt-upgrade-and-phased-updates/?_ga=2.188709921.821663753.1729358776-767678726.1724008001#how-does-it-actually-work)

---

### Post by georgesgiralt on 2024-10-19
Yes, I know that, but sometimes they are "stuck" for days, even weeks (happened once) so for no real reason...

---

### Post by 1fallen on 2024-10-19
The only way to get a clear answer is to file a bug report on "phased-upgrades" and you'll likely get multiple reply's by the team.

---

### Post by grahammechanical on 2024-10-19
Why do they have phrased updates? If an update starts breaking operating systems they can hold back the update until it is fixed. So the choice is a) send out the update to every machine at the same time and risk breaking Ubuntu on every machine it is installed on. Or, b) send out the update to 10% of the machines and if nothing gets broken send out the update to another 10% of the machines. And so on.

You may not like it but the maintainers of Ubuntu are making sure that most of your machines, if not all of them, remain operational because of phased updates.

Regards

---

