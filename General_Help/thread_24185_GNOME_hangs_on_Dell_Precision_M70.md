---
title: "GNOME hangs on Dell Precision M70"
date: 2005-04-05
forum: General Help
---

### Post by Pausanias on 2005-04-05
When I boot the live CD, everything is great... video card, wireless DHCP network, everything is detected. The brown screen comes up at the best possible resolution. The mouse pointer comes up, and I can move it around. The Ubuntu music plays. And then.....

Nothing. I can move the cursor around but nothing else happens. Just a pure brown background on the screen.

After 5 minutes' wait, there's activity on the CD drive again. But nothing changes.

I tried switching my wireless adapter off in the BIOS and rebooting. Same thing.

Dell Precision M70
NVIDIA Quadro FX 1400
1GB RAM
60  GB 7200 RPM Hard Drive
Intel Wireless PRO a/b/g

---

### Post by Pausanias on 2005-04-05
Same thing happens with Kubuntu. Cursor, white screen, and that's it.

Help!

---

### Post by Pausanias on 2005-04-05
MEPIS Live CD works fine on this system. However, I would really like to use Ubuntu and GNOME. Any ideas why MEPIS works but both Ubuntu and Kubuntu live CDs hang.

Come on, tell me it's just a matter of setting one of the boot options and everything will work fine. :sad:

EDIT: could it be due to Xorg/XFree differences?

---

### Post by Pausanias on 2005-04-06
I solved the problem myself.

It was with the nv driver. The nv driver doesn't work.

I did a full install of hoary, and switched from the nv to the nvidia driver. Now everything works fine.

I note that I had the same exact problem three years ago with the nv driver on my Inspiron 4100. Switching to the nvidia driver fixed everything.

I'm sorry, but that driver is a piece of junk.

---

### Post by koreth on 2005-04-09
Same problem for me -- my video card is an Nvidia GeForce 6800. Any chance of an updated LiveCD that uses the other driver? I don't think I want to take the time to do a real install just to evaluate whether I want to take the time to do a real install!

---

### Post by cayblood on 2005-11-23
[QUOTE=Pausanias]I solved the problem myself.

It was with the nv driver. The nv driver doesn't work.

I did a full install of hoary, and switched from the nv to the nvidia driver. Now everything works fine.
[/QUOTE]

Forgive my ignorance, but how do you switch the driver?  Do you simply edit the X configuration or do you have to install a package for the nvidia driver too?

Thanks

---

### Post by Pausanias on 2005-11-23
[QUOTE=cayblood]Forgive my ignorance, but how do you switch the driver?  Do you simply edit the X configuration or do you have to install a package for the nvidia driver too?

Thanks[/QUOTE]

[https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70](https://wiki.ubuntu.com/InstallingUbuntuOnADellPrecisionM70)

---

### Post by cayblood on 2005-11-23
Thanks!

---

