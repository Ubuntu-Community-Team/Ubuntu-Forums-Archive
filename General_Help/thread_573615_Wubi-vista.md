---
title: "Wubi-vista"
date: 2007-10-11
forum: General Help
---

### Post by anonymous j on 2007-10-11
Tried everything, literally to install wubi, but after the ubuntu splash screen my computer just stops working, no loading of the OS, nothing. I have a windows Vista Home Premium compaq notebook, any help is appreciated.

---

### Post by ago on 2007-10-12
Does that happen after the second reboot? I.E. after the stage where you see all the red progress bars? In this case it is probably due to the wrong video driver being used. 

ALT+F2
sudo dpkg-reconfigure xserver-xorg
select vesa driver, that is enough to show the graphical environment than look for guides specific for your card

If you are brave you may also try the new version: [http://wubi-installer.org/devel/minefields](http://wubi-installer.org/devel/minefields)

---

### Post by anonymous j on 2007-10-12
No, my laptop only reboots once, and I never see a red progress bar, is there soemthing i missed?

---

### Post by anonymous j on 2007-10-12
just tried the link you provided, once i get to the ISO download part, the progam quits unexplectedly

---

