---
title: "problems with Wine"
date: 2005-08-24
forum: General Help
---

### Post by pink_ego_b0x on 2005-08-24
hey, 
When i try and install wine i get 

The following packages have unmet dependencies:
  wine: Depends: libwine (= 0.0.20050310-1.1) but 0.0.20050419-1~5.04ubp1 is to be installed
E: Broken packages

i have installed libwine. any one have any idea whats up?
cheers
tom

---

### Post by Koba on 2005-08-24
[QUOTE=pink_ego_b0x]hey, 
When i try and install wine i get 

The following packages have unmet dependencies:
  wine: Depends: libwine (= 0.0.20050310-1.1) but 0.0.20050419-1~5.04ubp1 is to be installed
E: Broken packages

i have installed libwine. any one have any idea whats up?
cheers
tom[/QUOTE]
 try this:
```
sudo apt-get -f install
```or```
sudo apt-get clean
```
and then try installing the program again.

---

### Post by TiMBuS on 2005-08-25
[http://www.ubuntuforums.org/showthread.php?t=56892&highlight=apt+wine](http://www.ubuntuforums.org/showthread.php?t=56892&highlight=apt+wine) go here. you dont have the repositories

---

