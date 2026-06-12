---
title: "cannot use apt-get install"
date: 2008-04-14
forum: General Help
---

### Post by gianhut on 2008-04-14
i don't know why but i could never use apt-get install <package name>. it always tell me that it doesn't know the packages i'm looking for.

i tried uncommenting the sources  in /ect/apt/source.list ..... and I'm using Kubuntu 7.10

---

### Post by kellemes on 2008-04-14
What packages?

---

### Post by gianhut on 2008-04-14
any package. such as compiz-core, firefox ,libstdc++5... I've been having to search and download the packages manually, it's pretty painful because of the package dependancies.

---

### Post by az on 2008-04-14
Post the output of

sudo apt-get update
and
sudo apt-get install (any package you want to install)

---

### Post by ScorpKing on 2008-04-14
you can alway search for a package with aptitude search <packagename> and it will display the available packages.

---

