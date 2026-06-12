---
title: "Can't compile"
date: 2007-05-16
forum: General Help
---

### Post by steam_engenius on 2007-05-16
Hello I'm running Kubuntu right now and whenever I try to run 'make' or 'make install' it gives an error message, the most recent being:

-e  Doing 'make install'... 
Password: 
su: Authentication failure
Sorry.

-e  ERROR doing make install... 

I have build-essential installed and am not really sure what I should check next. I'm trying to install kbfx btw. Thanks a bunch!

---

### Post by kinghajj on 2007-05-16
try 'sudo make install' instead.

---

### Post by steam_engenius on 2007-05-16
It asks if I want to install as root and I entered yes then it requests a password and I enter it and I get that error message

---

### Post by taurus on 2007-05-16
Try

```
sudo aptitude update
sudo aptitude install checkinstall
./configure
make
sudo make checkinstall
```

---

