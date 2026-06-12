---
title: "Amarok on Ubuntu 6.06"
date: 2006-10-20
forum: General Help
---

### Post by marianom on 2006-10-20
I decide to try Amarok but first some questions in search of knowledge:
1- I understand Amarok is for KDE. How does it work with GNome? Any special advice regarding the installation process? The Amarok page says it works but if somebody can share his personal experience, I'll appreciate it.
2- Do you guys recommend installing the version from repositories (which I guess is lower than the official release) or, because interesting new features and fixes, should I try a newer version?

Thanks for all your answers.

---

### Post by Arby on 2006-10-20
Amarok will work just fine under Gnome. If you install it through Synaptic in the normal way then synaptic should handle the installation of all the kde libraries on which amarok depends for you. 

This is an argument for using the version of amarok that is in the repositories. If you compile amarok yourself from the amarok site you will have to deal with all the dependencies yourself which can be a pain

---

### Post by pay on 2006-10-20
```
gksudo gedit /etc/apt/sources.list
```
then add
```
# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main
```then```
sudo aptitude update
sudo aptitude install amarok
```and that will give you the newer version

---

### Post by Arby on 2006-10-20
Oooh didn't know about that. I'll be upgrading my amarok later:D

---

