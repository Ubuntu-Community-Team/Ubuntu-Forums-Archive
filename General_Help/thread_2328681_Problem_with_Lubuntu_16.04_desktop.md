---
title: "Problem with Lubuntu 16.04 desktop"
date: 2016-06-23
forum: General Help
---

### Post by arias-arian on 2016-06-23
HOla!
Hi!
WHen I log, my desk does not appear.
The following is displayed:

[ATTACH=CONFIG]269740[/ATTACH]


thx for your time

---

### Post by vasa1 on 2016-06-23
It looks like you're logging into a **Lubuntu Netbook** session!

Make sure you log into plain **Lubuntu**.

---

### Post by arias-arian on 2016-06-23
OK vasa1 
that works.

thx man!

---

### Post by vasa1 on 2016-06-23
You're welcome!

The login screen remembers the last chosen desktop choice.
In my case, I have four choices:
```
07:15 AM ~ $ ls /usr/share/xsessions
Lubuntu.desktop  Lubuntu-Netbook.desktop  LXDE.desktop  openbox.desktop
07:15 AM ~ $ 
```


 So if you just enter your password and press <enter>, you'll be logging into the desktop you (or whoever accessed your machine) last chose.

---

