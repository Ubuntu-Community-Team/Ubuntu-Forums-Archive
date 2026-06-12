---
title: "Desktop randomly crashes with linux (Xubuntu and Kubuntu), but Windows runs OK."
date: 2018-03-09
forum: General Help
---

### Post by mfisher91 on 2018-03-09
I'd previously been experiencing problems running Xubuntu (16.04 and 17.10) on my desktop. The issue is that the PC randomly freezes (sometimes takes an hour, other times it may last for a couple of days) and I have no control - no keyboard or mouse input (including system rescue commands). Even the reset button on my desktop doesn't work, I have to hold the power button to turn the machine off. The other issue is that when I tried to reinstall Xubuntu (rather than upgrading), I received I/O errors. Due to this, work gave me an identical machine to work on, and it experienced the exact same issues.

Our PC repairers came out to fix it and after replacing the SSD, memory and motherboard, finally got it working...until it crashed a few days later and started repeating the cycle again. We then decided to send the PC into them and they (again) replaced the SSD and memory, installed Windows and soak testing the machine for 2 days. The end result was that it was working, so they sent it back to us. I repeated the soak test for a further two days and as there was no random crashing, installed Kubuntu (17.10)....to find it had crashed when I got into work the next morning. I've since tried to reinstall Kubuntu to remove any extras that I've installed, but I started receiving the I/O errors again.

I'm confused as to what could be causing this. My gut feeling is that it's a Linux driver, but I could be wrong. My system specs are below:

```
kubuntu@kubuntu:~$ inxi -ACDMNSG
System:    Host: kubuntu Kernel: 4.13.0-21-generic x86_64 bits: 64 Desktop: KDE Plasma 5.10.5
           Distro: Ubuntu 17.10
Machine:   Device: desktop Mobo: ASUSTeK model: PRIME B250M-A v: Rev X.0x serial: N/A
           UEFI: American Megatrends v: 1001 date: 12/11/2017
CPU:       Quad core Intel Core i7-7700 (-HT-MCP-) cache: 8192 KB
           clock speeds: max: 4200 MHz 1: 3600 MHz 2: 3600 MHz 3: 3600 MHz 4: 3600 MHz 5: 3600 MHz 6: 3600 MHz
           7: 3600 MHz 8: 3600 MHz
Graphics:  Card: Intel HD Graphics 630
           Display Server: x11 (X.Org 1.19.5 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) version: 4.5 Mesa 17.2.2
Audio:     Card Intel 200 Series PCH HD Audio driver: snd_hda_intel Sound: ALSA v: k4.13.0-21-generic
Network:   Card-1: Realtek RTL8192CE PCIe Wireless Network Adapter driver: rtl8192ce
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 1008.2GB (0.8% used)
           ID-1: /dev/sda model: ST1000DM010 size: 1000.2GB
           ID-2: USB /dev/sdb model: SD/MMC size: 7.9GB
```

Any help would be gratefully received :).

---

### Post by QIII on 2018-03-09
Hello!

In the interest of diagnosis, could you install 16.04 and let us know how that goes?  I'm not finding any obvious recent bug reports for Plasma 5.10.5 on 17.10 that look quite the same.

Cheers.

---

### Post by kerry_s on 2018-03-09
you also might want to try disabling some of the animations.
in xubuntu: settings-> window tweaks-> composting
kubuntu: settings-> display & monitor-> compositer

---

