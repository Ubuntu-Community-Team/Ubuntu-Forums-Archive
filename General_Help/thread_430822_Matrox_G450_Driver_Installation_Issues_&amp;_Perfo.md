---
title: "Matrox G450 Driver Installation Issues &amp; Performance"
date: 2007-05-02
forum: General Help
---

### Post by Kadin2048 on 2007-05-02
I'm trying to get my Matrox Millenium G450 AGP card working well on 6.06 LTS, and I'm running into some issues.

There have been a few threads about the G450 in the past, but none of them seem to deal with this issue, or else they were abandoned / never answered.

Here's the situation: I have an IBM Intellistation M Pro, a pretty basic P4 workstation. In it is a Matrox  Millenium G450 DVI (that's the version with the single DVI output, not dual-head). It's a 32MB card. Not exactly the greatest thing in the world, but serviceable.

Anyway, I installed Xubuntu 6.06 LTS (just because that's the CD I had lying around). It works, but the performance seems to be really terrible -- much worse than I think it ought to be, even for a 32MB card.

In particular, if I drag a window around the desktop, it's very, very choppy. Scrolling is also not very smooth. I know this card isn't brand new -- but seriously, it ought to be able to at least move windows around without moving in 1" jumps, shouldn't it?

Anyway, I thought maybe the problem was in the open-source 'mga' driver, so I downloaded the latest proprietary driver that Matrox lists for this card. This is "matrox_driver-x86_32-4.4.0.tar.gz". I opened it up, and ran 'sudo ./install.sh' and I get an error: "ERROR: Could not find X server driver install path."

I don't know if the Matrox 4.4.0 driver is just so old, that it won't install onto a modern Xorg system, or if there's some other problem.

Questions:
1) Is the Matrox-supplied driver (from their website, v.4.4.0) the same as the "mga" opensource driver provided with Ubuntu? In other words, is it worth trying to get this thing installed, or am I just installing something I already have? I'm not interested in doing it, if there's not going to be a performance benefit.

2) Am I right in thinking that the performance of this card shouldn't suck as much as it does? It's a card designed specifically for 2D performance ... I don't give a crap about 3D, I don't play games or anything, but it drives me crazy to have a system that can't even scroll or move windows around the desktop smoothly.

3) Has anyone ever used this card, and gotten it to work well? By 'well,' I mean working smoothly, at some reasonable, modern resolution like 1280x960 or 1280x1080? Or should I just chuck it and get an Nvidia FX 5200?

---

### Post by skred77 on 2007-06-28
Hi

I don't know if the proprietary driver available in the matrox site if better, but at least it's newer.
I haven't measured the performance, but i would be interested if somebody weould do that.

If you want to install the driver, find out your x version
```
[root@dhcppc1 /]# X -version
```
for me, it was
X Window System Version 7.0.0
Release Date: 21 December 2005

Then locate your driver. In my box, FC5, it was located at /usr/lib..., not /usr/X11r6, like the install.sh expects...
```
212 -rwxr-xr-x 1 root 207772 Feb 12  2006 /usr/lib/xorg/modules/drivers/mga_drv.so
```

Then check the installation package (X version is needed here):
```
[root@dhcppc1 /]$ ls -lasg /home/xxx/Desktop/matrox_driver-x86_32-4.4.0/xserver/7.0.0/mga_*
236 -rw-r--r-- 1 xxx230234 Apr 25  2006 matrox_driver-x86_32-4.4.0/xserver/7.0.0/mga_drv.o
256 -rwxr-xr-x 1 xxx 251956 Apr 25  2006 matrox_driver-x86_32-4.4.0/xserver/7.0.0/mga_drv.so
368 -rw-r--r-- 1 xxx 367476 Apr 25  2006 matrox_driver-x86_32-4.4.0/xserver/7.0.0/mga_hal_drv.o
392 -rwxr-xr-x 1 xxx 392051 Apr 25  2006 matrox_driver-x86_32-4.4.0/xserver/7.0.0/mga_hal_drv.so
```

Ok, the driver is newer, so let's backup the old driver, install new drivers and ensure they are in correct place and have correct rights.
```
[root@dhcppc1 /]# mv /usr/lib/xorg/modules/drivers/mga_drv.so.old /root/usr-lib-xorg-modules-drivers-mga_drv.so
[root@dhcppc1 /]# cp matrox_driver-x86_32-4.4.0/xserver/7.0.0/*.so /usr/lib/xorg/modules/drivers/
[root@dhcppc1 /]# ls -lasg /usr/lib/xorg/modules/drivers/mga*
256 -rwxr-xr-x 1 root 251956 Jun 28 15:33 /usr/lib/xorg/modules/drivers/mga_drv.so
392 -rwxr-xr-x 1 root 392051 Jun 28 15:33 /usr/lib/xorg/modules/drivers/mga_hal_drv.so
```

Now newer driver is in the correct place. All left to do is to boot and configure X.

---

### Post by Kadin2048 on 2007-06-28
Thanks a bunch there, skred! I'll give it a shot and see what happens.

Unfortunately I don't have the exact system I was using before to test it on (I got a little frustrated with the Intellistation so I swapped its Matrox card out for an Nvidia with TV-Out and turned it into a MythTV appliance...) but as soon as I get something that can take the Matrox again, I'll definitely try that.

Great HOWTO.

---

### Post by skred77 on 2007-07-09
You may want to check out also later drivers not from Matrox. Check out my post @ blenderforum. [http://www.blender.org/forum/viewtopic.php?t=11900](http://www.blender.org/forum/viewtopic.php?t=11900)

-S

---

