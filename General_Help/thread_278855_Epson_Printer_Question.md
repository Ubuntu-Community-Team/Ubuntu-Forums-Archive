---
title: "Epson Printer Question"
date: 2006-10-17
forum: General Help
---

### Post by cssutto on 2006-10-17
I just bought an Epson R1800 Printer and it will not print text in black.

Text is sort of a dark gray, but I want BLACK.

Even text that has been set as bold is not black.

I have tried dinking with the density settings in printer properties, but I can't change it to black.

Help will be appreciated.

Ubuntu Dapper.

CSSJR

---

### Post by cssutto on 2006-11-22
Bump

---

### Post by tames on 2007-05-12
Has anyone successfully printed to an R1800 printer, with the correct black density? Any tips on getting this to work? I can print a properly-centered document, but as cssutto describes, the blacks on a text document are a dark gray, not really black. The print driver density settings (and all of the settings for that matter) appear to have no effect on the output print quality. I don't believe the problem is in the printer, as when booted up into Windows, blacks are a deep black, and photos print out in true photo quality.

tames

---

### Post by tames on 2007-05-13
Update: acc. to the gutenprint forum, the gutenprint 5.0.0-rc2 driver (included with ubuntu) is out of date, and had problems with the R1800. The source code is available for recomended version 5.0.0 or 5.0.0.99.1, which I downloaded and compiled/installed, but there is significant manual configuration changes to get this to work, acc. to the docs. May just wait for the compiled binary in convenient package form, unless someone has a suggestion...

---

### Post by IanW on 2007-05-13
Fiesty comes with version 5.0.0.99.1 as standard. There may be a backport available for Edgy?

---

### Post by tames on 2007-05-13
Hmmm, I have 7.04 installed as a separate "experimental" installation, on a different disk drive, and it shows the same 5.0.0-rc2 gutenprint driver (and no 5.0.0.99.1 or 5.0.0 package available, acc. to synaptic).

---

### Post by nounours18200@free.fr on 2007-07-01
I have also a pb  with Gutenprint version 5.0.1-2 on Kubuntu 7.04. 
I have downloaded "gutenprint-5.0.1-1lsb3.1.i486.rpm", then I have trabsformed it in a ".deb" package using Alien, and then installed it.

> Here is the install report:

root@elodie:~# dpkg --unpack gutenprint_5.0.1-2_i386.deb
Sélection du paquet gutenprint précédemment désélectionné.
(Lecture de la base de données... 106874 fichiers et répertoires déjà installés.)
Dépaquetage de gutenprint (à partir de gutenprint_5.0.1-2_i386.deb) ...
root@elodie:~# apt-get install -f
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances
Lecture de l'information d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
1 partiellement installés ou enlevés.
Il est nécessaire de prendre 0o dans les archives.
Après dépaquetage, 0o d'espace disque supplémentaires seront utilisés.
Paramétrage de gutenprint (5.0.1-2) ...
* Restarting Common Unix Printing System: cupsd                         [ OK ]

The pb is: when I try to install my printer (Epson R1800 and Epson 890) by going to "system setting / printer / add", there is still no mention of these drivers . The printers are recognized byt Kubuntu, but I do not the appropriate drivers.

I have posted a message on the French Kubuntu forum, but no reply...

Has someone an idea of what I should do ??

thanks

---

