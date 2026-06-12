---
title: "update error downloading 7.10"
date: 2007-11-03
forum: General Help
---

### Post by rmadd on 2007-11-03
I am trying to upgrade to 7.10 and receive the following error: (ERROR During Update:  A problem occured during the update, this is usually some sort of network problem, please check your network connection and retry.) There is nothing wrong with my network, I have my laptop on the same network, and it updated fine no problem. I hope there is someone with the fix of this problem. So far I haven't seen much user friendly with Ubuntu. Thanks for your help.

---

### Post by Maestro23 on 2007-11-03
Please post your sources.list

> cat /etc/apt/sources.list

---

### Post by rmadd on 2007-11-03
Maestro23's Avatar 
 	
Maestro23 , I am not real linux savvy, what am I suppose to do with this link after opening it in terminal? Thanks for your reply. RM

---

### Post by Maestro23 on 2007-11-03
> **rmadd said:**
> Maestro23's Avatar 
 	
Maestro23 , I am not real linux savvy, what am I suppose to do with this link after opening it in terminal? Thanks for your reply. RM

Use your mouse to highlight the complete text and copy/paste it here in the forum.

---

### Post by rmadd on 2007-11-03
I finally figured out what you wanted. Thanks for your patience.

## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

---

### Post by rmadd on 2007-11-04
I got the problem resolved, I reloaded ubuntu, and worked fine. Thanks for your help.

---

