---
title: "Upgrade to Gutsy gone all wrong."
date: 2007-10-21
forum: General Help
---

### Post by Architeuthis on 2007-10-21
I just upgraded to Gutsy. The problem is my wireless doesn't work anymore (I new this would happen because I tested the live cd, but I thougth I would be able to manually install and compile the driver). For some reason the wrong drivers are selected so I tried to compile the right ones myself. (rt2570). But I don't seem to able to compile them (it could on Feisty). 
This is the output: 

> rt2570-1.1.0-b2/Module/rtusb_main.o
/home/architeuthis/Desktop/rt2570-1.1.0-b2/Module/rtusb_main.c: In functie &#8216;usb_rtusb_probe&#8217;:
/home/architeuthis/Desktop/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: fout: &#8216;dev_base&#8217; undeclared (first use in this function)
/home/architeuthis/Desktop/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: fout: (Each undeclared identifier is reported only once
/home/architeuthis/Desktop/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: fout: for each function it appears in.)
/home/architeuthis/Desktop/rt2570-1.1.0-b2/Module/rtusb_main.c:1905: fout: &#8216;struct net_device&#8217; has no member named &#8216;next&#8217;
make[2]: *** [/home/architeuthis/Desktop/rt2570-1.1.0-b2/Module/rtusb_main.o] Fout 1
make[1]: *** [_module_/home/architeuthis/Desktop/rt2570-1.1.0-b2/Module] Fout 2
make[1]: Map '/usr/src/linux-headers-2.6.22-14-386' wordt verlaten
rt2570.ko failed to build!
make: *** [module] Fout 1


Strange thing is the upgrade doesn't seem to have finished 100%.

A huge submenu has been created under "Applications" called "Overige" (Dutch for remaining) it's filled with all sorts of things like "X-server", "Cache" and "Cookies" of which only half of them even have an icon. I don't know where these come from, I didn't have them before. The system seems to be very active all the time (when I look at the systemmonitor, it looks like I'm compiling all the time). The normal cursor (which I saw on the live cd) seems to be gone.

To me it just looks like the updated was only completed partially, so does anyone know how I could complete the upgrade or why I can't compile the driver?

---

### Post by Happy_Man on 2007-10-21
Hmmm... yeah, you're right, your upgrade does show some symptoms of having borked halfway through. Check your CD for faults, and if it's good, try to install again. As for your driver compilation, I can only suggest that It was not written for Gutsy, and that may be causing some errors.

---

### Post by Architeuthis on 2007-10-21
> Check your CD for faults, and if it's good, try to install again. 
I didn't use the cd to upgrade, I upgraded with the update manager.
I just discovered another error, I don't have any sound anymore, although my "C-Media usb Audio" boxes are detected.

---

### Post by Happy_Man on 2007-10-21
Well, then my first point is still valid. Upgrading through a package manager never went well for me. My suggestion would be to back up anything important (if you don't already have a /home partition) and reinstall. Using a CD.

If you don't have a separate /home, use the instructions from the link in my sig to make one. They really come in handy during times like these.

---

### Post by Architeuthis on 2007-10-22
I'm going to follow your advice and make a separate home partion and then I'll reinstall. Thanks for the advice!

---

