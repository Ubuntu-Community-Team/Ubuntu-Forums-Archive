---
title: "can't find files/programs"
date: 2008-06-19
forum: General Help
---

### Post by RC84 on 2008-06-19
Im trying to enable desktop effects and having problems trying to fix that. In reading the how to enable it says to check Restricted Driver Manager under Admisitrator but I don't even have Restricted Driver Manager. Also,can't find any nVidia restricted drivers. I used Add/Remover to get the newest nVidia driver and when I go to Hardware drivers it doesn't even show the driver I installed listed.?  Am I missing something?

Im sort of new. Im been learning things myself(find it the only way to learn how to do something) but hitting a wall on this.Thank you!

---

### Post by TeoBigusGeekus on 2008-06-19
Right click the System menu and select customize menus. See if restricted driver manager is listed and check it to show up.

---

### Post by Nameless_one on 2008-06-19
Also, I think Restricted Driver Manager is a new feature, added in Feisty or Gutsy I think. If you are running Dapper or some older version, it's probably not there.

---

### Post by RC84 on 2008-06-19
right clicked on System and then edit menu. Went to Admisitrator menue everything is checked but no Restricted Driver Manager even listed to check or uncheck.

I have Ubuntu 8.04 LTS. How do I go about getting it and getting the driver installed? Im running a 20inch monitor and running in 800x600 and bugging me lol

---

### Post by RC84 on 2008-06-21
Still can't figure this out. Trying to ignore the fact that I have to use a 800x600 resolution on a 20inch monitor. 

I have tried the solutions in the above posts with no luck

---

### Post by drs305 on 2008-06-21
If you aren't sure you have the nvidia driver installed, you can try to install the nvidia drivers with envyng-gtk:
```
sudo aptitude install envyng-gtk
```

---

