---
title: "Xubuntu drains battery fast and overheats"
date: 2013-02-04
forum: General Help
---

### Post by aajjbb on 2013-02-04
Hello all.

I've already searched for a lot of places, and none of them got me a real solution or a possible workaround. I have a Asus K45VM with an GForce GT 630M with 2GB. I've already read about the problems with *buntus and this nvidia graphics, but the point is, I've already now that the problem with overheat and outrageous battery consumption is related to the both graphics(Intel integrated and Nvidia GForce), but there's a real way to solve it ? I don't do any kind of 'hard' graphic effort in my Xubuntu installation so use only my Intel graphics should be okay.

There's a way to make them work efficiently or a 'healthy' way to turn off my gforce and only use my integrated graphics ?

---

### Post by Calinou on 2013-02-04
The easy way (not always possible): go to your BIOS/UEFI menu after booting your laptop and check if you can disable the integrated (or dedicated -- I get to laugh at the 630M) graphics card.

The harder way: install Bumblebee (do not install the NVIDIA driver by hand, it'll be installed by Bumblebee automagically).

---

### Post by aajjbb on 2013-02-06
Thank you so much, bumblebee made my battery increases more than 2 hours.

---

