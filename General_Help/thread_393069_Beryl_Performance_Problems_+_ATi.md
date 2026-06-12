---
title: "Beryl Performance Problems + ATi"
date: 2007-03-25
forum: General Help
---

### Post by schwartzki on 2007-03-25
Ok guys, I am fairly new to beryl but I have it running on my machines (after a few kernal panics) but now the problem I am having is performance issues, choppy even tho beryl is running

In terminal beryl is showing:
bschwartzki@schwartzki-desktop:~$ beryl
************************************************** ************
* Beryl system compatiblity check *
************************************************** ************

Detected xserver : XGL

Checking Display :1.0 ...

Checking for XComposite extension : passed (v0.3)
Checking for XDamage extension : passed
Checking for RandR extension : passed
Checking for XSync extension : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0


Here is an copy of my xorg.conf file:

Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
Driver "fglrx"
BusID "PCI:1:0:0"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "XAA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode "x8"
Option "AGPFastWrite" "on"
EndSection

Section "Monitor"
Identifier "FPD2275W"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. ATI Default Card"
Monitor "FPD2275W"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection

I am running a ATI Radeon X1650Pro 256MBGDDR3
System is running a gig of ram and while beryl is running, performance is choppy.

Thanks for any help

---

