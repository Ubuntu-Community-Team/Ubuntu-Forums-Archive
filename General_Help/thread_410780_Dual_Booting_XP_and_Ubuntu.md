---
title: "Dual Booting XP and Ubuntu"
date: 2007-04-16
forum: General Help
---

### Post by coolzgeek on 2007-04-16
I installed XP for gaming and Ubuntu for general work and entertainment on 2 separate SATA HDs. I placed GRUB in the MBR of my Ubuntu HD(160GB)on IDE channel 3 and installed XP on a 80 GB hd. When the computer boots, the GRUB menu shows up and when I boot Ubuntu, it is in an SH terminal while XP works fine. I do not really know of any SH commands as i use BASH. Please help

---

### Post by Paul41 on 2007-04-16
Did you install the server version of Ubuntu? The desktop version should boot to a GUI.

---

### Post by zvacet on 2007-04-16
If you find out that you installed serveer version don´t worry.If you want desktop 

for GNOME
```
sudo aptitude install ubuntu-desktop
```

and for KDE

```
sudo aptitude install kubuntu-desktop
```

---

### Post by Andyfield123 on 2007-04-16
There are different options in GRUB and one of them starts up Ubuntu in the Kernal are you sure you have chosen the correct one?

---

### Post by coolzgeek on 2007-04-17
I installed the Desktop edition and i think the terminal is in SH

---

### Post by coolzgeek on 2007-04-21
I installed the alternate version.

---

### Post by coolzgeek on 2007-04-27
Got it! You have to edit menu.lst for grub. Here's the link : [http://morecode.wordpress.com/2007/02/17/dual-booting-between-windows-and-linux-on-separate-hard-disks/](http://morecode.wordpress.com/2007/02/17/dual-booting-between-windows-and-linux-on-separate-hard-disks/)

---

