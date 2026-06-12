---
title: "ATI graphics help"
date: 2007-04-17
forum: General Help
---

### Post by FeelTherush1 on 2007-04-17
i am attempting to run the live cd but keep getting the error message of "Failed to start x server (graphical interface) it may not be set up correctly." i know that my ATI Radeon X800 GTO (AGP) is not fully supported in ubuntu....is there any way i can get this to work out for me or do i have to trash my ATI card for this to work?

---

### Post by kornhead127 on 2007-04-17
After X failing it should dump you back to a terminal. If not press <ctrl><alt>F1. and type this...
```
sudo dpkg-reconfigure xserver-xorg
```
Set it up. and select the ati driver. Once you're done you'll be back at the terminal. type...
```
sudo nano /etc/X11/xorg
```
and scroll to the device section and replace the driver ati with radeon. The radeon driver supports the x800 so you should be Ok. For more information on getting your card set up go here
[http://www.die.net/doc/linux/man/man4/radeon.4.html]("http://www.die.net/doc/linux/man/man4/radeon.4.html")

---

### Post by Erlander on 2007-04-18
Another option with the live cd is to select Safe Graphics Mode at the startup menu.

Rob

---

### Post by FeelTherush1 on 2007-04-18
> **Erlander said:**
> Another option with the live cd is to select Safe Graphics Mode at the startup menu.

Rob

safe graphics dont work for me... i donno. thanks anyways

---

