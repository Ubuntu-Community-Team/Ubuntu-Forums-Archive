---
title: "Geforce 5600 FX Dual Monitors"
date: 2008-04-18
forum: General Help
---

### Post by tommy1987 on 2008-04-18
Hello,

I have a GeForce FX 5600 card and two monitors plugged into it. I have the Nvidia driver installed and cannot manage to set up the other screen to try. Every time I edit xorg.conf to try to configure my other monitor X does not usually start. On the one screen everything is normal but on the other it is flashing crazy colors and changing depending on what is on my main screen. For instance, if I open a different program the colours might change around, it is like a disco light :-)

Please help :-)

Thanks in advance.

---

### Post by tommy1987 on 2008-04-18
When using the proprietary driver from Nvidia X will not start and I have to restore the backup to get X. If this helps? Please help everything is configured perfectly in Vista with no effort whatsoever.

---

### Post by Az_135r on 2008-04-18
are the monitors the same?

do you use $ nvidia-settings?

the way i done it was to use nvidia-settings, configure dual screens for twinview, set resolutions and frequency, then save, logout and login

compiz works too :)

---

### Post by tommy1987 on 2008-04-18
When I install the proprietary driver X won't start. The problems in /var/log/Xorg.0.log are as follows (My method of install is letting the OS choose the driver as recommended and it chooses the latest NVIDIA graphics cards driver):

(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)

Isn't it obvious that the path will not load since it has two slashes or is that just me?

What should I do, since I really want to utilize the power of my graphics card. The only way I am able to boot into X now is to set the driver to 'nv' which truly sucks.

Thank you very much!

---

### Post by tommy1987 on 2008-04-19
bump.. Please help :-(

---

