---
title: "Xorg &quot;via&quot; driver broken"
date: 2005-04-07
forum: General Help
---

### Post by teevee on 2005-04-07
Since upgrading to the latest Xorg packages yesterday (6.8.2-10) the "via" driver appears to be broken. I used this driver in Warty and also in Hoary without any problems ever since I upgraded to it a few weeks ago. X now only displays at 640x480 (with funky waves at the edges, probably due to wrong h-sync settings).

dpkg-reconfigure xserver-xorg didn't help.

Xorg.0.log shows the following:
> 
....cut.....
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "via"
(II) VIA(0): [drm] drmOpen failed
(EE) VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
(II) VIA(0): - Visuals set up
(II) VIA(0): VIAInternalScreenInit
(II) VIA(0): - B & W
(II) VIA(0): Using 1567 lines for offscreen memory.
(II) VIA(0): Using XFree86 Acceleration Architecture (XAA)
.....cut.....
Let me know if you want the complete X log (long) or my xorg.conf (although I doubt the problem is in there since it worked before, and I didn't change it).

---

### Post by nad on 2005-04-08
Unfortunately, the best way for someone else to help diagnose your problem is for you to post your config and log files. If you post your log file from only your last login it will be much shorter.

It looks like you are using the CastleRock chip (CLE266). This chip uses the unichrome (via) driver from the unichrome project at sourceforge.net. DRI is not implemented yet and there may be new problems with the latest drivers. Please look at your xorg log (cat /var/log/Xorg.0.log | grep -i unknown) and see if the your card ID is unknown. If it is, notify the project that they may include the ID in their new driver.

Dan M

---

