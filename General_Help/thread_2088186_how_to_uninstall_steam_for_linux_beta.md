---
title: "how to uninstall steam for linux beta"
date: 2012-11-25
forum: General Help
---

### Post by hunterkasy on 2012-11-25
I am running ubuntu 12.10 and I installed steam for linux beta, but now I want it removed but I cant find it in the software center

---

### Post by Francisco Cardoso on 2012-11-25
sudo dpkg -r steam.deb

Hope it helps.

Francisco

---

### Post by hunterkasy on 2012-11-26
> **Francisco Cardoso said:**
> sudo dpkg -r steam.deb

Hope it helps.

Francisco

This is what I get:

dpkg: error: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
tyler@tylermain:~$

---

### Post by mstock2 on 2012-11-26
Made an account just to say this: to uninstall the steam package, run
```
sudo apt-get remove steam
```

---

