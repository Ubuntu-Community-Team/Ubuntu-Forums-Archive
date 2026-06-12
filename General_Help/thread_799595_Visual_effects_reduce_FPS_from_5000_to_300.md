---
title: "Visual effects reduce FPS from 5000 to 300"
date: 2008-05-19
forum: General Help
---

### Post by Maratonda on 2008-05-19
Hi, 
I have an ATI Radeon 9200 SE on Ubuntu 8.04, therefore I am using open source drivers.
With visual effects turned off, glxgears does not flicker and outputs around 5000 fps.
With visual effect set to normal, glxgears looks pretty sluggish and flickers a lot, with 300 fps. When I drag the glxgears window around, the windows multiply.
This is xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Any help would be immensely appreciated, as I am a newbie.
There are other similar posts describing the problem on the web, but I didn't manage to find one with a solution.
Thanks.

---

### Post by Forlong on 2008-05-19
Two words: so what.

Do not care about glxgears' output. Ever. It varies when changing the theme.
If Compiz works satisfactorily for you, then all is good. :)

---

### Post by Maratonda on 2008-05-19
you're right, the point is that with visual effects on scrolling in Firefox is too slow...I thought the things were related...

---

### Post by Forlong on 2008-05-19
Did you install Xgl (you shouldn't)?
Did you try to install anything else in the past?
Because that's the first time, I hear somebody complaining about slow scrolling in Fx with the ati/radeon driver -- that's generally a fglrx issue.

---

### Post by Maratonda on 2008-05-19
I looked in synaptic.
No package related to Xgl is installed.
However, searching for fglrx returns the package
> Non-free Linux 2.6.24 modules on x86/x86_64 
This package provides restricted modules for Linux version 2.6.24 on
x86/x86_64.

Currently the following modules are included:
 - madwifi (Atheros)
** - fglrx (ATI)**
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 - fcdsl, fcdslusba, fcusb, fwlanusb, fxusb (AVM ISDN x86 only)

These modules are "restricted" because they are not available under a
completely Free licence.

There is another guy with the same problem (if he solved it, I don't know). In this thread (post #64 onwards):
[http://ubuntuforums.org/showthread.php?t=764633]("http://ubuntuforums.org/showthread.php?t=764633")
this is the first post
[http://ubuntuforums.org/showpost.php?p=4850517&postcount=64]("http://ubuntuforums.org/showpost.php?p=4850517&postcount=64")
Thanks for you time, forlong.

---

### Post by Forlong on 2008-05-19
Can you please run [Compiz-Check]("http://ubuntuforums.org/showthread.php?t=799070") so we can get more info?

---

### Post by Maratonda on 2008-05-19
Looks clean to me...
>  Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


So I shouldn't uninstall that package I was mentioning before?

---

### Post by Forlong on 2008-05-19
No, do not remove the package -- it just provides **kernel modules**, not the actual driver.

I just read the thread you linked above and it really seems to be related to your graphics chip.
There may be some settings for the xorg.conf to tweak things for you but unfortunately, I don't know much about this.

You should consider starting a separate thread about this or ask a moderator to change the title of this one.

---

### Post by Maratonda on 2008-05-19
Thanks a lot for your help!

---

### Post by jklm988 on 2008-05-19
[&#26080;&#32447;&#32593;&#26725;](http://www.szwx.cn/products.php?id=146) [&#26080;&#32447;&#32593;&#32476;&#20135;&#21697;](http://www.szwx.cn/products.php?id=146) [&#26080;&#32447;&#23485;&#24102;&#35774;&#22791;](http://www.szwx.cn/newsshow.php?id=65)[&#28595;&#22823;&#21033;&#20122;&#30041;&#23398;](http://www.do360.com/country/australia-index.asp) [&#1075;&#1088;&#1072;&#1085;&#1080;&#1090;](http://www.suntoway-stone.com)

---

### Post by markbuntu on 2008-05-19
Right click on the Compiz Fusion Icon and look at the compiz options. 

Is indirect rendering greyed out and checked?
If so, that is why compiz is so slow.
I do not know if your card or the open source drivers support direct rendering but I think not.

You can also run the compiz benchmark which you can enable in the compiz settings manager. If it is below about 100 you will have these problems.

Compiz, when using indirect rendering puts a huge load on the cpu and will slow down every process. Scrolling is a function that compiz oversees when it is running and it is very cpu intensive even without compiz trying to run on top so eveything slows way down.

I switched to from Hardy 386i to amd64 and compiz runs much better now with far less cpu loading. I also stopped using firefox.

HP 1330n Media Center (modified)
ASUS A8AE-LE motherboard (OEM)
AMD Athlon64 3800+ 2.9GHZ 939 socket
3GB 3200 DDR RAM
ATI Radeon Express 200M (disabled in bios)
ATI HD3650 1GB DDR2  PCI Express
AC97 on board sound
Realtek 810L

SOYO 24 inch LCD wide screen monitor 1920x 1200
Samsung 930B 19 inch LCD 1280x1024


Ubuntu 8.04 "Hardy Heron" - Release amd64
Kernel Linux 2.6.24-16-generic
ATI Proprietary Linux Driver Version Identifier:8.47.3
Big Desktop, Compiz, Emerald

---

### Post by Maratonda on 2008-05-20
> **markbuntu said:**
> 
Is indirect rendering greyed out and checked?

Yes, now I understand...

> I do not know if your card or the open source drivers support direct rendering but I think not.

Direct rendering is enabled. I can run visual effects, but they're slow.

Thanks for your help, at least now I understand why that's happening. :)

---

