---
title: "script/program that dumps entire hardware configuration to file"
date: 2008-02-10
forum: General Help
---

### Post by mnem0 on 2008-02-10
Every now and then I find machines on which Ubuntu does not boot properly. Issue can be no sound or no graphics or whatever. To file a really good bug report it's of course useful to include information about the hardware on the relevant machine and I know that the Ubuntu wiki has great descriptions of how to get such info (running "lspci" etc etc). I've done these steps several times but it's quite a lot of work so I'm looking for something automated.

The ALSA project has an absolutely amazingly easy way to do this (their script can be downloaded here: [http://hg.alsa-project.org/alsa/log/tip/alsa-info.sh](http://hg.alsa-project.org/alsa/log/tip/alsa-info.sh) ) but this only covers audio devices. I'm looking for something similar which covers all kinds of hardware.

Basically, I want the script or tool or dump all attached PCI devices with their IDs, and also all attached USB devices with their IDs etc. And I guess, if it's possible for ISA devices, harddrives etc.

Whether the data is stored to file (or to pastebin as the ALSA script does) doesn't really matter.

Does anyone know of such a script/tool?

---

### Post by astoltz on 2008-02-10
Try "lshw".  I think that's what you're after.

---

### Post by mnem0 on 2008-02-11
Yea that works. Thanks!!

---

