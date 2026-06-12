---
title: "Synaptic broke on a reparation attempt"
date: 2007-04-03
forum: General Help
---

### Post by Psykotik on 2007-04-03
I'm gone really in trouble with ubuntu, for the first time in 8 months use. I hope someone would be able to help me, since I cannot use synaptic anymore.

Firstly, I had had some troubles with last OpenOffice upgrade; for every new update I install, Synaptic answered after the update this kind of message:

```
Une erreur est survenue
Les détails suivant sont fournis :

E: ttf-opensymbol: le sous-processus post-installation script a retourné une erreur de sortie d'état 4
E: openoffice.org-core: problèmes de dépendances - laissé non configuré
E: python-uno: problèmes de dépendances - laissé non configuré
E: openoffice.org-writer: problèmes de dépendances - laissé non configuré
E: openoffice.org-calc: problèmes de dépendances - laissé non configuré
E: openoffice.org-draw: problèmes de dépendances - laissé non configuré
E: openoffice.org-impress: problèmes de dépendances - laissé non configuré
E: openoffice.org-math: problèmes de dépendances - laissé non configuré
E: openoffice.org-base: problèmes de dépendances - laissé non configuré
E: openoffice.org: problèmes de dépendances - laissé non configuré
E: openoffice.org-evolution: problèmes de dépendances - laissé non configuré
E: openoffice.org-gtk: problèmes de dépendances - laissé non configuré
E: openoffice.org-gnome: problèmes de dépendances - laissé non configuré
E: openoffice.org-common: problèmes de dépendances - laissé non configuré
E: openoffice.org-java-common: problèmes de dépendances - laissé non configuré
E: openoffice.org-style-default: problèmes de dépendances - laissé non configuré
E: openoffice.org-style-industrial: problèmes de dépendances - laissé non configuré
```

Well, it was bothering but I wasn't stuck. Anyway, following an advice, I tried to downgrade two libraries (previously downloaded from ubuntu repository) suspected to be the source of the problem:

```
sudo dpkg -i --force-downgrade  libfontconfig1_2.3.2-7ubuntu2_i386.deb

sudo dpkg -i --force-downgrade  fontconfig-config_2.3.2-7ubuntu2_all.deb

```

Geeesh, why on earth did I send theses commands ? Synaptic is now unusable, saying some libraries (libfontconfig1-dev, libpango1.0-0, libpango1.0-common and beagle) are broken. Install, update, uninstall are no more possible, since whenever I try to do so ALL the ubuntu packages are selected to be uninstalled, in addition to the action selected.

Any idea?

---

### Post by Rui Pais on 2007-04-03
Hi,
on synaptic have you clicked on 'Custom Filters' (at bottom left) and choose the 2nd entry from the List 'Broken'? Double click any package listed (color red). Sorry don't know the names that appear on French... 

You could also, try on a console:
```
sudo aptitude -f install
```
or
```
sudo apt-get -f install
```

hth

---

