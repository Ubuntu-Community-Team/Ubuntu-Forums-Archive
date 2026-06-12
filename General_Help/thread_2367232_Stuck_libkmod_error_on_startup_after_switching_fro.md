---
title: "Stuck: libkmod error on startup after switching from NVIDIA to Intel graphics card"
date: 2017-07-27
forum: General Help
---

### Post by xyrxs on 2017-07-27
Hello,

I recently installed ubuntu 16.04 on my laptop and after installing all the NVIDIA drivers, finally got Ubuntu to boot when I set the graphics card to MSHYBRID in the BIOS menu. However, after changing the PRIME profile in NVIDIA X Server Settings to use the Intel GPU (Power Saving Mode), I am unable to start Ubuntu in MSHYBRID mode (it only boots properly in DISCRETE). When I boot in MSHYBRID mode I get stuck on a screen with the following message: 

[INDENT]libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modeprobe.d/tuxedo-wmi.conf line 1: ignoring bad line starting with 'Options'[/INDENT]
[INDENT=2]lvmetad is not active yet, using direct activation during sysinit[/INDENT]
[INDENT]libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modeprobe.d/tuxedo-wmi.conf line 1: ignoring bad line starting with 'Options'
/dev/mapper/ubuntu--vg-root: clean, 488554/14712832 files, 9143649/58847232 blocks
[/INDENT]

I checked the tuxedo-wmi.conf file and deleted the text there (something I entered from a mod for the clevo keyboard backlighting), the file is now empty however I still get stuck on the same error during startup. I didn't receive this error before changing to the Intel GPU in the X Server settings and while I get the libkmod error on startup in DISCRETE mode, it still brings me to the login screen and I can use Ubuntu normally.

Any suggestions? This is the first time I've used Linux in a very long time so I'm a bit rusty.


Laptop: Clevo p650hs-g, NVIDIA GTX 1070 and Intel HD Graphics 630, i7-7700HQ
Ubuntu 16.04

---

