---
title: "Jammy : why Evince is not able to open links in firefox snap and Thunderbird can ?"
date: 2023-09-13
forum: General Help
---

### Post by georgesgiralt on 2023-09-13
Hello Guys !
Almost everything is in the title of this post. 
When I get an email with a link in it, when I click on the link, it open a new tab in Firefox. Fine. 
When I open a PDF file in Evince, and there is a link in this file, now, the link does not open in Firefox anymore. 
As this PDF file is quite old and I used it a lot, I *know* that it worked before my upgrade to Jammy... So I bet this has to do with the Firefox snap....
How do I change this behaviour ? 
Many thanks in advance for your help !
Have a nice and bright day.

---

### Post by #&amp;thj^% on 2023-09-13
There was a bug report a few months back:[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1794064/comments/2](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1794064/comments/2)

The posters solution was to un-install evince and re-install. (.deb package)
the point I took away from it was you need either Evince and your browser from APT, or both from snap.
BTW Okular from apt worked as well.

---

### Post by georgesgiralt on 2023-09-13
Hello and thank you for your answer.
I do not understand what you state. Maybe my bad English is the culprit.
What I have : 
```
snap list
Nom                        Version           Révision  Suivi            Éditeur        Notes
bare                       1.0               5         latest/stable    canonical&#10003;     base
canonical-livepatch        10.6.0            235       latest/stable    canonical&#10003;     -
chromium                   116.0.5845.179    2614      latest/stable    canonical&#10003;     -
core                       16-2.60.2         15925     latest/stable    canonical&#10003;     core
core20                     20230801          2015      latest/stable    canonical&#10003;     base
core22                     20230801          864       latest/stable    canonical&#10003;     base
cups                       2.4.6-4           980       latest/stable    openprinting&#10003;  -
firefox                    117.0-2           3068      latest/stable    mozilla&#10003;       -
gnome-3-38-2004            0+git.efb213a     143       latest/stable/…  canonical&#10003;     -
gnome-42-2204              0+git.ff35a85     126       latest/stable    canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511   1535      latest/stable/…  canonical&#10003;     -
snap-store                 41.3-71-g709398e  959       latest/stable/…  canonical&#10003;     -
snapd                      2.60.3            20092     latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.9               83        latest/stable/…  canonical&#10003;     -
# dpkg -l evince
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom            Version       Architecture Description
+++-==============-=============-============-=================================
ii  evince         42.3-0ubuntu3 amd64        Document (PostScript, PDF) viewer
# apt install --reinstall evince
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
0 mis à jour, 0 nouvellement installés, 1 réinstallés, 0 à enlever et 10 non mis à jour.
Il est nécessaire de prendre 301 ko dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Réception de*:1 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 evince amd64 42.3-0ubuntu3 [301 kB]
301 ko réceptionnés en 1s (441 ko/s)
(Lecture de la base de données... 491091 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../evince_42.3-0ubuntu3_amd64.deb ...
Dépaquetage de evince (42.3-0ubuntu3) sur (42.3-0ubuntu3) ...
Paramétrage de evince (42.3-0ubuntu3) ...
Traitement des actions différées («*triggers*») pour bamfdaemon (0.5.6+22.04.20220217-0ubuntu1)*...
Rebuilding /usr/share/applications/bamf-2.index...
Traitement des actions différées («*triggers*») pour desktop-file-utils (0.26-1ubuntu3)*...
Traitement des actions différées («*triggers*») pour hicolor-icon-theme (0.17-2)*...
Traitement des actions différées («*triggers*») pour gnome-menus (3.36.0-1ubuntu3)*...
Traitement des actions différées («*triggers*») pour libglib2.0-0:amd64 (2.72.4-0ubuntu2.2)*...
Traitement des actions différées («*triggers*») pour man-db (2.10.2-1)*...
Traitement des actions différées («*triggers*») pour mailcap (3.70+nmu1ubuntu1)*...
```
And the link in a PDF (from Lenovo, Hardware Maintenance Manual)....
Could you, please clarify for me ? 
Thanks.

---

### Post by #&amp;thj^% on 2023-09-13
In short, both the browser and Evince either have to be snaps or .debs.
To make clear, Firefox snap and Evince .deb is not a good mix.
I still suggest Okular

---

### Post by georgesgiralt on 2023-09-13
Will try this and report back. Today had been a very very long day. 
Thanks.

---

### Post by georgesgiralt on 2023-09-15
So, here I am again. 
As I spend days having my password manager work in snap Firefox, I did not want to go back to a Deb version of Firefox. (as this will be somewhat temporary, as it is against the current of the river). So I thought to switch my Evince to snap. 
```
$ snap search evince
Nom     Version  Auteur            Notes  Résumé
evince  44.1     ken-vandine&#10026;      -      Document viewer for popular document formats

```
But, I was stopped by the Author name. I would have thought it was Canonical. And as the snap are here to enforce security (well not just this, but), I decided not to go for it. 
So as suggested, I tried Okular. And it works directly out of the box. 
When you click on a link in a PDF document in Okular, it opens a new tab in your favourite browser and shows you the content of this link. Perfect. 
I've now just to change the default app to open PDF files in my settings... 
Thanks to all who responded and gave advices.

---

