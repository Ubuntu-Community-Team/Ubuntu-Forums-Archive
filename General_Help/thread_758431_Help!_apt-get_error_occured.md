---
title: "Help! apt-get error occured"
date: 2008-04-18
forum: General Help
---

### Post by knivla on 2008-04-18
the problem is.

any software i install then i will get this error.


E: /var/cache/apt/archives/rar_1%3a3.7b1-2_i386.deb: files list file for package `screensaver-default-images' contains empty filename

---

### Post by PmDematagoda on 2008-04-18
Execute:-
```
sudo apt-get clean
```
to see if that won't solve your problem.

---

### Post by knivla on 2008-04-18
sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by sekinto on 2008-04-18
Do you have another package managing program running?

---

### Post by knivla on 2008-04-18
i reboot the system and and performt the sudo apt-get clean and sudo apt-get autoclean

and still doesn't work in add/remove or in apt-get install ....



:confused:

---

### Post by knivla on 2008-04-18
sudo apt-get clean
[sudo] password for alvin:

sudo apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done

---

