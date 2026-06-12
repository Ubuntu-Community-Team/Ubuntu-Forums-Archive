---
title: "X fails upon start everytime, have to reinstall NVIDIA each time."
date: 2007-02-09
forum: General Help
---

### Post by xjas05 on 2007-02-09
everytime i reboot my computer... X attempts to start but fails, i have to now keep the NVIDIA installer on my desktop, and i have to install it each time i reboot, in order for X to work... anyone had this problem?.. takes awhile having to install it at each boot

---

### Post by nickoli_02 on 2007-02-09
After you install the NVIDIA driver do you run:

```
sudo dpkg-reconfigure xserver-xorg
```

and select your driver in the list to use? That might be the problem, worth a try.

---

### Post by xjas05 on 2007-02-09
tried that, but then it starts asking me where on the PCI it is, how is a newbie supposed to know all this gunk? seriously.. for the simplest of all things, its the equivalent of climbing mount everest...

---

### Post by nickoli_02 on 2007-02-11
I've had to reconfigure xserver many times for reinstalling the ATI drivers, and every time it automatically detects the location of the video card. Try pressing next or ok, and if it really needs you to tell it where the video card is try using the default 1:0:0.

---

### Post by Gibbs on 2007-02-11
This has happened to me too. I used a program called [Envy]("http://albertomilone.com/nvidia_scripts1.html"), uninstalled my drivers and then installed. Worked a treat and it does everything for you.

---

### Post by JeyKey on 2007-02-11
happened to me too, but this helped:
sudo apt-get remove linux-restricted-modules-`uname -r`

---

