---
title: "Monitor Resolution"
date: 2017-03-16
forum: General Help
---

### Post by rbscairns on 2017-03-16
What I have is:

```
System:    Host: CEBPC01 Kernel: 4.4.0-67-generic i686 (32 bit)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK product: B202
           Mobo: ASUSTeK model: P5LD2EB-DHS v: Rev 1.xx
           Bios: American Megatrends v: 1204 date: 11/26/2009
CPU:       Single core Intel Atom N270 (-HT-) speed/max: 800/1600 MHz
Graphics:  Card: Intel Mobile 945GSE Express Integrated Graphics Controller
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.00hz
           GLX Renderer: Mesa DRI Intel 945GME x86/MMX/SSE2
           GLX Version: 1.4 Mesa 12.0.6
Network:   Card: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
Drives:    HDD Total Size: 320.1GB (61.0% used)
Info:      Processes: 137 Uptime: 25 min Memory: 487.8/991.6MB
           Client: Shell (bash) inxi: 2.2.35
``` 

Monitor is ASUS VH202T

This is a dual boot system. In Windows I can set the monitor resolution to 1280x768 and all looks good. In Lubuntu I only have the options of 1028x768, 800x600, 848x480 and 640x480.

How can I set the monitor resolution to 1280x768 as the default resolution?

---

### Post by TheFu on 2017-03-17
Does **xrandr** show that resolution?

---

### Post by rbscairns on 2017-03-20
xrandr returns

> Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
DVI1 unknown connection (normal left inverted right x axis y axis)
   1360x768      59.80  
   1152x864      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

My desired 1280x768 is not listed. My connection is VGA1

---

### Post by efflandt on 2017-03-20
Is there some reason that you are not using DVI? That is a digital connection which could read the EDID of the monitor to tell which video modes it supports, and would typically default to the 1600x900 of your monitor. But it would also make it easier to choose other video modes it supports.

VGA is analog, so Linux cannot tell what video modes it has. If you want to change that you would typically run **cvt 1280 720 60** or **gtf 1280 720 60** to find a modeline and then try one or the other with xrandr commands. Like:```
xrandr --newmode "1280x720" 74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --addmode VGA1 1280x720
xrandr --output VGA1 --mode 1280x720
```But I only did something like that when connecting a laptop to a 1080p HDTV, so I would put such commands in a script that I would run manually. But I am not sure how to add and set a mode like that automatically.

---

### Post by TheFu on 2017-03-20
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) should be helpful.

Use your favorite editor to create ~/.xprofile containing something like:

    **xrandr --output VGA1 --mode 1280x768 --rate 60**
Logout and login. If that doesn't work, switch to a different console, login and remove the ~/.xprofile file.  I didn't test this myself, just following the instructions from that page.

My laptop drives 2 monitors.  1 via VGA and the other through HDMI.  The VGA connection goes through a KVM switch (keyboard, video, mouse), so I'd have to change all the cabling and connections and some of the video cards don't support anything except VGA. My point is that you shouldn't feel bad using VGA.

---

