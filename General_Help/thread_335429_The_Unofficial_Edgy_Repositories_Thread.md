---
title: "The Unofficial Edgy Repositories Thread"
date: 2007-01-10
forum: General Help
---

### Post by kpkeerthi on 2007-01-10
Apologies if I'm in the wrong forum category.

If any of you use any of the unofficial Edgy repositories, please post the repository information in the format as below. This would help consolidate all unofficial repositories in one thread. 

1. sources.list entry.
For e.g.
```

deb http://ubuntu.beryl-project.org/ edgy main

```

2. GPG key (if applicable)
For e.g.
```

wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -

```

3. List of packages the repository provide

**PS: Please post only Edgy repos**

---

### Post by depele on 2007-01-13
==> would be nice ! I am looking for a good stable sources.list file.

---

### Post by Uncle Spellbinder on 2007-01-31
Here's my *sousces list* which include some "unofficial" repos:

```
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg –keyserver subkeys.pgp.net –recv KEY
#  gpg –export –armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget URL –quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE
#

### Ubuntu supported packages ###
# (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted
deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-proposed main restricted

### Ubuntu community supported packages ###
# (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-security universe multiverse

### Ubuntu backports project ###
# (GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

### CANONICAL COMMERCIAL REPOSITORY ###
# (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu edgy-commercial main

### Medibuntu ###
# (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

### Seveas' Ubuntu packages ###
# Packages is this repository can be gpg authenticated. The key that is being used for signing the # packages is 1135D466.
# wget http://seveas.imbrandon.com/1135D466.gpg -O- | sudo apt-key add -
deb http://seveas.imbrandon.com edgy-seveas all
deb-src http://seveas.imbrandon.com edgy-seveas all

### Automatix2 ###
deb http://www.getautomatix.com/apt edgy main

### Debuntu ###
# wget http://repository.debuntu.org/GPG-Key-chantra.txt
# sudo apt-key add GPG-Key-chantra.txt
# rm GPG-Key-chantra.txt
deb  http://repository.debuntu.org/ edgy multiverse
deb-src http://repository.debuntu.org/ edgy multiverse

### Malteo's repository v6.10 ###
# wget http://malteo.homelinux.net/B54820BC.gpg -O- | sudo apt-key add -
deb http://malteo.homelinux.net edgy-malteo all
deb-src http://malteo.homelinux.net edgy-malteo all

### Listen ###
#deb http://theli.free.fr/packages/ edgy listen
```

---

