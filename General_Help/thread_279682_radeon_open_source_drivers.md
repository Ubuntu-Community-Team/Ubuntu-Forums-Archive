---
title: "radeon open source drivers"
date: 2006-10-18
forum: General Help
---

### Post by Architeuthis on 2006-10-18
Hello, i have an ati radeon 9250 and i would like to try the open source radeon drivers, since the fglrx driver doesnt support my card anymore and the older versions contain some bugs.

So how do i make them work:
i found out i had to replace "ati" with "radeon" in the device section in this file: /etc/x11/xorg.conf. I saw examples of other people using the radeon drivers but they have a lot of other options too. How exactly should i make these drivers work?

---

### Post by Architeuthis on 2006-10-19
Can someone help me? Have i posted this in the wrong section? Really i'm desperate.

---

### Post by t.n. on 2006-10-19
There is no distinction between "ati" and "radeon" anymore, if I remember this correctly. I think the driver automatically detects your card and uses the right one.
As to the options, you do not need any for basic usage. Just use Driver "ati".

There are many options available (and some are required) if you want 3D acceleration. You can search the forums for this. But first I would try to get the card running without any options. If this works, you try enabling 3D acceleration.

---

### Post by dbd on 2006-10-20
> **t.n. said:**
> There is no distinction between "ati" and "radeon" anymore, if I remember this correctly. I think the driver automatically detects your card and uses the right one.

I *think* that this is wrong, and that ati will always be used by default, and that radeon has to be chosen by you (if you want 3D acceleration.)

Anyway, t.n.'s advice to get basic 2D working first by choosing ati is good. But if you want radeon there is a guide here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by podunk on 2006-10-20
I have the Radeon 9200, and used method 1 on this page:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Method 2 doesn't work with older cards, ATI no longer supports us.

---

### Post by Architeuthis on 2006-10-23
> I *think* that this is wrong, and that ati will always be used by default, and that radeon has to be chosen by you (if you want 3D acceleration.)

Anyway, t.n.'s advice to get basic 2D working first by choosing ati is good. But if you want radeon there is a guide here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks this is wat i needed, i tried some options in my device section in xorg-xconf but that gave me an "unsupported video mode". I dont know which options i can enable with my card, any help?

> I have the Radeon 9200, and used method 1 on this page:
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Method 2 doesn't work with older cards, ATI no longer supports us.
I dont want to use those proprietary drivers because they are unethical :) , and they contain bugs so some 3d programs crash frequently.

---

### Post by Architeuthis on 2006-10-23
> Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"radeon"
	Option          "AGPMode"       "4"
        BusID		"PCI:1:0:0"
EndSection

This is my device section in /etc/X11/xorg.conf. Which other options should i use and will all options listed in man radeon work with my card? 

> drmCommandWrite: -22
drmRadeonCmdBuffer: -22 (exiting)

This is an error i get every time i start a 3d program.

---

### Post by dbd on 2006-10-23
I'm not sure what options will work with your card, but I will post the options I use, although my card is a 9800 Pro, a very significantly different card (these drivers don't even give me full 3d support). But it may be helpful anyway:
> Section "Device"
Identifier      "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
Driver          "radeon"
BusID           "PCI:1:0:0"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "EXA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPFastWrite" "on" <-prevents  X from starting when enabled
EndSection

I also have these options at the end of xorg.conf:
> Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by Architeuthis on 2006-10-24
> Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver		"radeon"
	Option          "AGPMode"       "4"
        BusID		"PCI:1:0:0"
        Option          "ColorTiling" "on"
        Option          "AccelMethod" "EXA"
        Option          "RenderAccel" "true"
EndSection

I updated my xorg.conf file to this, but i still get this error when i start a 3d app.

> drmCommandWrite: -22
drmRadeonCmdBuffer: -22 (exiting)


I get the same bug when i execute glxgears, so i assume i have done something wrong.

---

