---
title: "Synaptic wont let me install anyhting because of previous crash, here's the error:"
date: 2008-01-25
forum: General Help
---

### Post by optimisteo on 2008-01-25
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/classpath/+question/23041](https://answers.launchpad.net/ubuntu/+source/classpath/+question/23041) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all!

Synaptic crashed while i was trying to uninstall java and install gcjwebplugin (at the same time, is this the cause for conflict? i don't know)

Then it didn't work anymore, and suggested i should type in a shell: dpkg --force -a or something in this style, which i did.

ever since then, synaptic recovered but has been unable to install ANY package i select (ending on a error)

Here's the error (in French - then translated)

E: /var/cache/apt/archives/iceape-browser_1.1.5-1ubuntu0.7.10_amd64.deb: la liste des fichiers pour le paquet « classpath-gtkpeer » contient un nom de fichier vide

which means: " the file list for package « classpath-gtkpeer » contains the name of a empty file. "

So it seems the problem arises from package « classpath-gtkpeer », but i have no idea how to fix it...

I then tried this, but with not any more success than before:

Code:
iram@Suntzu:~$ sudo apt-get remove -f classpath-gtkpeer
[sudo] password for iram:
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances
Lecture des informations d'état... Fait
Les paquets suivants seront ENLEVÉS : (translation: packages removed)
  cacao classpath classpath-gtkpeer gcjwebplugin
0 mis à jour, 0 nouvellement installés, 4 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0o dans les archives.
Après dépaquetage, 2826ko d'espace disque seront libérés.
Souhaitez-vous continuer [O/n] ? o
(Lecture de la base de données... dpkg : erreur de traitement de gcjwebplugin (--remove) : (trans: error handling gcjwebplugin )
 la liste des fichiers pour le paquet « classpath-gtkpeer » contient un nom de fichier vide : (trans:the file list for package classpath... contains the name of an empty file.
dpkg: ../../src/packages.c:252: process_queue: l'assertion « !queuelen » a échoué. (trans: « !queuelen » failed)
E: Sub-process /usr/bin/dpkg exited unexpectedly

I went into apt cache and clicked « classpath-gtkpeer » which didn't work (other packages did work)

Thanks for your help, it is much appreciated.

:)

Opti

---

### Post by dcstar on 2008-01-25
> **optimisteo said:**
> 
..........
E: **/var/cache/apt/archives/iceape-browser_1.1.5-1ubuntu0.7.10_amd64.deb**: la liste des fichiers pour le paquet « classpath-gtkpeer » contient un nom de fichier vide
...........

```
gksudo nautilus
```

And then delete that file.

---

