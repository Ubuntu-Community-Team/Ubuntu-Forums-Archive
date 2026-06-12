---
title: "Terminal_update-manager"
date: 2018-06-23
forum: General Help
---

### Post by Freiklite on 2018-06-23
Hi,
I installed xubuntu 18.04 TLS.
The software updater works but the "sudo apt-get update  && apt-get upgrade" command doesn't.
The terminal answer is:> ~$ sudo apt-get update  && apt-get upgrade
Atteint:1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic InRelease
Atteint:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Atteint:3 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Atteint:4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Lecture des listes de paquets... Fait
E: Impossible d'ouvrir le fichier verrou /var/lib/dpkg/lock - open (13: Permission non accordée)
E: Impossible de verrouiller le répertoire d'administration (/var/lib/dpkg/). Avez-vous les privilèges du superutilisateur ?


The system doesn't unlock the /var/lib/dpkg file and the /var/lib/dpkg/ repertory.
Can you help me?
Thanks for your attention,
Ciao

---

### Post by TheFu on 2018-06-23
You are missing the 2nd **sudo**, which is required.
the '&&' separates 2 commands and runs the 2nd only if the first completes without errors.

Run 
```
sudo apt update
sudo apt upgrade
```
or 

```
sudo apt update && sudo apt upgrade
```

---

### Post by kazakore on 2018-06-23
If dkpg is locked are you sure you don't have a graphical software manager of some sort open as well? Synaptic, Gnome Software Centre etc etc.

Or if you have updates set to run automatically, as is standard on a new install, then it may be using it to upgrade in the background and thus locked out.

If anything is using the dpkg service than nothing else can until it has finished.

---

### Post by Freiklite on 2018-06-23
Hi,
Thanks  very much for your answers.
The command:> sudo apt update && sudo apt upgrade
has  fixed my problem.
Thanks again,
Ciao.

---

