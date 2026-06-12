---
title: "Heat in 15.10"
date: 2015-11-30
forum: General Help
---

### Post by Andi_Abdul_Syukur on 2015-11-30
ok now i'm using 15.10 following the suggestion from my first thread  [http://ubuntuforums.org/showthread.php?t=2304827](http://ubuntuforums.org/showthread.php?t=2304827). when i'm using 10.04  my laptop doesn't get hot very much the max i get 74C and i play pcsx1.  but when i try 11.04 and above i don't know what's going on it gets 93C  in 30min while idle and gets hang. i have installed thermald and tlp  nothing solved, and i change tlp with laptop-mode it still hots. i try  xubuntu-desktop, lubuntu-desktop, kubuntu-desktop from this  [http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available/65108#65108](http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available/65108#65108)  and still no change.

my laptop spesification is ASUS A46C, intel corei5, Nvidia GT635M, 4GBRam,

---

### Post by Vladlenin5000 on 2015-11-30
Have you installed the proprietary nvidia drivers? If not perhaps you should.
System Settings > Software properties > Additional drivers. Choose the recommended one, apply, reboot and test.

---

### Post by Andi_Abdul_Syukur on 2015-11-30
of course. there are 2 drivers i installed in hardware devices intel and nvidia and as an addition i update all the packages. although i don't use it, brightness very low 1 min and the screen turns black but still hot. it happens when in 11.10 the max 90C when the first unity is implemented.

---

### Post by sandyd on 2015-12-01
May be something hitting the CPU

Try running
```

top
```
in the terminal - is there anything using excessive CPU?

---

