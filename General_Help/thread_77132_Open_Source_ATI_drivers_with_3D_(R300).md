---
title: "Open Source ATI drivers with 3D (R300)"
date: 2005-10-16
forum: General Help
---

### Post by Psy-Q on 2005-10-16
The [R300 project]("http://r300.sourceforge.net") aims to bring Open Source 3D acceleration to modern ATI graphics cards. The latest version offer stable enough acceleration for Radeon 9600 and 9800 chipsets that they've been included in the DRI (CVS so far).

Are there plans to bringing this to standard Ubuntu anytime soon, or did someone perhaps write docs for non-intrusively adding this to a Breezy installation?

It would be great fun, as you can't use ATI's own driver properly on laptops because that one's known to break suspend/resume.

---

### Post by TheRazor on 2005-11-07
I've tried to get this working, and found that the X.org included in Breezy does not have the r300 patch applied.

So I rebuilt the *whole* X.org tree with the r300 patch just to get a new version of the package xserver-xorg-driver-ati. I'll make the package available here:

[http://www.linuxusers.de/ubuntu/files/xserver-xorg-driver-ati_6.8.2-77_i386.deb]("http://www.linuxusers.de/ubuntu/files/xserver-xorg-driver-ati_6.8.2-77_i386.deb")

Before I forget: <smallprint>This package works for me, but will not necessary do so for others. Use at your own risk.</smallprint>

This, together with a kernel new enough (2.6.14 works for sure, probably 2.6.13 development kernels as well) you can get direct rendering to work.

I found this Gentoo howto helpful:
[http://forums.gentoo.org/viewtopic-t-374745.html]("http://forums.gentoo.org/viewtopic-t-374745.html")

Good luck and have fun!
TheRazor

---

### Post by colinleroy on 2005-12-08
Nice, but I think there's something missing, probably /usr/lib/dri/r300_dri.so

After updating to your package, I have 
(II) RADEON(0): Direct rendering enabled

in /var/log/Xorg.0.log, but glxinfo still says "Direct rendering: no".

Thanks,
Colin

---

### Post by chele on 2006-03-16
r300 dri enabled by default on a new install of Dapper Flight 5,  13 march 2006.
This was on an HP nw8000 laptop with a radeon 9600 (ati firegl t2)

---

### Post by Psy-Q on 2006-04-06
That's excellent news, I can't wait to try it on a T42. Ubuntu are really pushing forward these days.

---

### Post by Psy-Q on 2006-04-16
chele: Did you verify that acceleration actually works? I tried with my Radeon Mobility 9600 in the T42. While Xorg.0.log says 

(WW) RADEON(0): Enabling DRM support

        *** Direct rendering support is highly experimental for Radeon 9500
        *** and newer cards. The 3d mesa driver is not provided in this tree.
        *** A very experimental (and incomplete) version is available from Mesa CVS.
        *** Additional information can be found on [http://r300.sourceforge.net](http://r300.sourceforge.net)
        *** This message has been last modified on 2005-08-07.

And then:

(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled


glxinfo | grep direct returns:

direct rendering: No

So can you verify that it works for you?


Update: Found a hint in this thread:

[http://www.ubuntuforums.org/showthread.php?t=110008&page=5](http://www.ubuntuforums.org/showthread.php?t=110008&page=5)

The upgrade has left a few old files hanging around, and Xorg's load order seems to have stopped at the wrong location? I linked the old location to the new /usr/lib/dri and now direct rendering works :)

---

### Post by chele on 2006-04-16
```
chele@brick:~$ glxinfo | grep direct

direct rendering: Yes
```:)

Next step is to try to get Xgl working....

---

