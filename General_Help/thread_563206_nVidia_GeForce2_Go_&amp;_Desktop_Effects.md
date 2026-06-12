---
title: "nVidia GeForce2 Go &amp; Desktop Effects"
date: 2007-09-29
forum: General Help
---

### Post by Job_314 on 2007-09-29
Hello forum members! I recently had some issues with my accelerated xgl drivers, but I've since been able to update Ubuntu, and get them working. When I enabled my desktop effects, after installing the drivers, I was asked to reboot. So, I did.

Instead of seeing my precious login screen I see a garbled tan screen that only covers half my monitor, so I re-installed Ubuntu and got it working my editing my /etc/X11/xorg.conf file...

But the actual issue that brings me to type this today, is since I've enabled my desktop effects, I don't see any title bars on my windows, nor do I see any scrollbars. Take the outside box off your windows, and image that... it's just the contents of the folder/window I see... No sides, or top, that's the best way I can explain it.

I tried to seek help on my machine, but when I boot Firefox, it's just a solid black cube... Any ideas?

My PC is a Dell Inspiron 2650 notebook, and is running Feisty.

PS, when I edited my xorg.conf file, I changed the "Device" section to this:
> Section "Device" 
Identifier "NVIDIA Corporation NV11 [GeForce2 Go]" 
Driver "nvidia" 
BusID "PCI:1:0:0" 
Option "DPMS" 
Option "NoLogo" "on"
Option "RenderAccel" "true" 
Option "NvAGP" "3" 
Option "UseEdidFreqs" "true" 
EndSection


---

### Post by Coolride on 2007-11-09
Go in the bios, and change the display to LCD only.

---

