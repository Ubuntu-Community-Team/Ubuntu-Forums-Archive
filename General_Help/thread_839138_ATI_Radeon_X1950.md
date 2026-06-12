---
title: "ATI Radeon X1950"
date: 2008-06-24
forum: General Help
---

### Post by linuxsudo on 2008-06-24
I can't seem to get suitable ATI Drivers for my card. Granted that Envy detects and installs the drivers for my card but these drivers are version 8.4 and they are not suitable as they lack the features which I need in 8.6. Also the 8.4 drivers crash on the latest Kernel update.

I tried running the ATI driver from the site and I installed it using a guide on the Internet, however once I restarted x after creating and installing the .deb packages, and after running xorg.conf I find that the display is all distorted, I can't post my xorg.conf because I'm at school right now.

Also in my xorg.conf I have no mode section under monitor, and there is also no drivers in the device section before running aticonfig --initial. There's never any mode section under this even after running aticonfig. 

My Monitor is detected as a CMC 17 and this is the link to monitor which I am using, that is assuming that my problems are related  to incorrect Monitor settings which I think that they are but I could be wrong. 

My Monitor is a Video Seven V7 E17PS More info here: [http://www.v7-world.com/showFile?fileID=19999381-a7d1-11db-9d0e-0015c5fb6342](http://www.v7-world.com/showFile?fileID=19999381-a7d1-11db-9d0e-0015c5fb6342)

---

### Post by pedro_orange on 2008-06-24
sudo dpkg-reconfigure -phigh xserver-xorg

Might sort ur problem with regards to specifying the display etc.
You'll wanna run this command after you've installed the drivers & closed x.
Ctrl+Alt+Fx & run it. Then restart gdm.

---

### Post by linuxsudo on 2008-06-24
Thanks but I tried that and it never worked.

---

### Post by avtolle on 2008-06-24
Try this; from the terminal```
gksudo displayconfig-gtk
```and see whether you can get your monitor configured.

---

