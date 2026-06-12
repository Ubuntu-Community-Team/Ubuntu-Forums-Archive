---
title: "Please Help Having Trouble With Beryl."
date: 2006-11-02
forum: General Help
---

### Post by JamesBlack on 2006-11-02
hi
i put beryl on my ubuntu 6.10
but it cant boot now because of beryl that doesnt worlk proprely
so i want to remove it from stratup programs using the console
could you tell me hoz to fix it
thkx

---

### Post by chriscando on 2006-11-02
Try booting into a terminal (failsafe) and sudo apt-get remove beryl
or modify your /etc/X11/xorg.conf to use the vesa or nv driver.
Thats what I would try, hope it helps

---

### Post by DoctorMO on 2006-11-02
We could do with a fail safe program to set xorg settings and clean up when people mess about with network/xorg/inputs/vital stuff.

---

### Post by Adrenal on 2006-11-02
Did you back up your xorg.conf file first?
If so you should be fine, just cp the backup to the same file name and location as the proper xorg.conf

---

