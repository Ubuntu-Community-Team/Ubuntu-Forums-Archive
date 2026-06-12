---
title: "Ubuntu Freezing"
date: 2007-12-23
forum: General Help
---

### Post by puleen on 2007-12-23
All of today I have been experiencing problems where Ubuntu 7.10 just freezes after I login. Once it freezes there is little I can do but restart the machine.

There has not been any hardware change for the past three months or so. At first I thought it was because of firefox, as I was trying to open firefox the three times that it froze. But, several tries later found out that even when I was working in just terminal, simply browsing through various directories, it would freeze as well.

Right now I am running MemTest86 to see if there are any memory problems. Apart from this can anyone suggest ways in which I can isolate and find out why the computer freezes?

A little information about the PC:

Asus P5N-E SLI motherboard
Intel Quad Core Q6600
OCZ Platinum Memory 2 X 1GB
HDD: WD 160 GB SATA, WD 250 GB SATA, WD 120 GB USB
DVD: Pioneer
Video Card: EVGA GeForce 8600 GTS 256MB

Additionally, I have a Windows XP partition that I keep for no official purpose. I logged into the Windows XP partition to see if the same freezing issue is OS related or hardware related. So far it has not happened within XP. So have been curious trying to find out what is happening.

Any suggestions would be appreciated.

Thanks,

---

### Post by PmDematagoda on 2007-12-23
How did you install the Nvidia driver?

Also this [thread]("http://ubuntuforums.org/showthread.php?t=617349") can help you a little, especially to reduce the chances of data corruption occurring due to the cold reboots.

---

### Post by puleen on 2007-12-23
For nVidia Drivers I followed one of the tutorials on the forum that explained how the installation. It was a pain simply because I was trying to get dual monitors working along with making sure that the drivers were installed and compiz worked as well.

Are you looking for something specific in regards to the nVidia driver install?

---

### Post by icechen1 on 2007-12-23
Sometimes,some buggy plugins in compiz freezes the system,so disable them or use the extra(or normal,none) in preferances>apparances.

---

### Post by PmDematagoda on 2007-12-23
Incidentally, what Nvidia driver version did you install? Was it 100.14.19 or 169.07?

---

### Post by puleen on 2007-12-23
I do not remember the driver version, is there a way to find out which version is currently running/installed?

Found it, 100.14.19 is what is displayed in the NVIDIA X Server Settings App.

NV-Control version: 1.13

The settings are configured to use TwinView with two monitors (both samsung 940B).

Thanks

---

### Post by puleen on 2007-12-23
I updated the drivers for nVidia, and still running into the same freezing problem.

The list of applications that I have running is:
1. Firefox (4 tabs)
2. Pidgin
3. XChat
4. Azureus

This is bizarre and really annoying....:mad:

---

