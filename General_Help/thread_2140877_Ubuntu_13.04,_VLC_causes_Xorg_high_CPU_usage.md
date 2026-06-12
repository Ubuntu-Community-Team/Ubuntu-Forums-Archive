---
title: "Ubuntu 13.04, VLC causes Xorg high CPU usage"
date: 2013-04-30
forum: General Help
---

### Post by FinalShot on 2013-04-30
Hey, I recently switched from 12.04 to ArchLinux and then back to 13.04, and yet this follows me everywhere. Either after some uptime doing nothing, or just watching a video in VLC, Xorg randomly starts using high amounts of my CPU, currently it's very slow/laggy to type this after closing VLC. If I reboot it goes away for a short amount of time, but it will return. I'm using VLC 2.0.6 and xorg 7.7?, also using nVidia 310 drivers.

If you need any more information is necessary I'll provide it, I need to fix this :( Thanks

---

### Post by Linuxisfast on 2013-05-01
Do you have proprietary nvidia drivers installed? In case you don't I suggest you add xswat-ppa and install the latest nvidia drivers. Also install nvidia-vdpau and then install latest vlc from [https://launchpad.net/~videolan/+archive/stable-daily](https://launchpad.net/~videolan/+archive/stable-daily) after updating vlc, make sure to tick use GPU in inputs and codecs section of VLC. In my nvidia, intel and amd machines, my CPU usage on HDMI movies is under 13% max.

---

### Post by FinalShot on 2013-05-02
Thanks for your help. I was using proprietary 310 drivers, now I'm using 313. I don't believe the cause of this is VLC as it just happened within 5 minutes after rebooting. Ubuntu became unusable after a little bit too, I couldn't click on anything, scroll, etc.

---

### Post by FinalShot on 2013-05-04
Bump. (24 hour bumps allowed?)

---

### Post by FinalShot on 2013-05-05
Well I've found something interesting in my Xorg log.

```
[  1858.752] [mi] Increasing EQ size to 512 to prevent dropped events.
(EE) BUG: triggered 'if (inSignalContext)'
(EE) BUG: ../../os/log.c:484 in LogVMessageVerb()
(EE) Warning: attempting to log data in a signal unsafe manner while in signal context.
Please update to check inSignalContext and/or use LogMessageVerbSigSafe() or ErrorFSigSafe().
The offending log format message is:
[xfixes] Barrier event queue full.  Dropping further events

(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7faa99760476]
(EE) 1: /usr/bin/X (LogVMessageVerb+0x195) [0x7faa9976b755]
(EE) 2: /usr/bin/X (ErrorF+0x8c) [0x7faa9976b98c]
(EE) 3: /usr/bin/X (0x7faa995b0000+0xebb4e) [0x7faa9969bb4e]
(EE) 4: /usr/bin/X (miPointerSetPosition+0x128) [0x7faa9974c218]
(EE) 5: /usr/bin/X (0x7faa995b0000+0x6cdec) [0x7faa9961cdec]
(EE) 6: /usr/bin/X (0x7faa995b0000+0x6dfc7) [0x7faa9961dfc7]
(EE) 7: /usr/bin/X (GetPointerEvents+0xe3) [0x7faa9961f503]
(EE) 8: /usr/bin/X (QueuePointerEvents+0x1d) [0x7faa9961f9ed]
(EE) 9: /usr/lib/xorg/modules/input/evdev_drv.so (0x7faa92175000+0x5f44) [0x7faa9217af44]
(EE) 10: /usr/bin/X (0x7faa995b0000+0x96927) [0x7faa99646927]
(EE) 11: /usr/bin/X (0x7faa995b0000+0xc0328) [0x7faa99670328]
(EE) 12: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7faa986b3000+0xfbd0) [0x7faa986c2bd0]
(EE) 13: (vdso) (0x7fff447c5000+0x70c) [0x7fff447c570c]
(EE) 14: (vdso) (__vdso_gettimeofday+0x161) [0x7fff447c5d01]
(EE) 15: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xf3a8e) [0x7faa928ffa8e]
(EE) 16: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x8007e) [0x7faa9288c07e]
(EE) 17: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xf7a0b) [0x7faa92903a0b]
(EE) 18: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xbb9e2) [0x7faa928c79e2]
(EE) 19: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x5580ec) [0x7faa92d640ec]
(EE) 20: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x52b819) [0x7faa92d37819]
(EE) 21: /usr/bin/X (BlockHandler+0x44) [0x7faa9960cb94]
(EE) 22: /usr/bin/X (WaitForSomething+0x114) [0x7faa9975d7f4]
(EE) 23: /usr/bin/X (0x7faa995b0000+0x58811) [0x7faa99608811]
(EE) 24: /usr/bin/X (0x7faa995b0000+0x4757a) [0x7faa995f757a]
(EE) 25: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7faa97300ea5]
(EE) 26: /usr/bin/X (0x7faa995b0000+0x478c1) [0x7faa995f78c1]
(EE) 
[xfixes] Barrier event queue full.  Dropping further events
(EE) BUG: triggered 'if (inSignalContext)'
(EE) BUG: ../../os/log.c:484 in LogVMessageVerb()
(EE) Warning: attempting to log data in a signal unsafe manner while in signal context.
Please update to check inSignalContext and/or use LogMessageVerbSigSafe() or ErrorFSigSafe().
The offending log format message is:
[xfixes] Barrier event queue full.  Dropping further events

(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7faa99760476]
(EE) 1: /usr/bin/X (LogVMessageVerb+0x195) [0x7faa9976b755]
(EE) 2: /usr/bin/X (ErrorF+0x8c) [0x7faa9976b98c]
(EE) 3: /usr/bin/X (0x7faa995b0000+0xebb4e) [0x7faa9969bb4e]
(EE) 4: /usr/bin/X (miPointerSetPosition+0x128) [0x7faa9974c218]
(EE) 5: /usr/bin/X (0x7faa995b0000+0x6cdec) [0x7faa9961cdec]
(EE) 6: /usr/bin/X (0x7faa995b0000+0x6dfc7) [0x7faa9961dfc7]
(EE) 7: /usr/bin/X (GetPointerEvents+0xe3) [0x7faa9961f503]
(EE) 8: /usr/bin/X (QueuePointerEvents+0x1d) [0x7faa9961f9ed]
(EE) 9: /usr/lib/xorg/modules/input/evdev_drv.so (0x7faa92175000+0x5f44) [0x7faa9217af44]
(EE) 10: /usr/bin/X (0x7faa995b0000+0x96927) [0x7faa99646927]
(EE) 11: /usr/bin/X (0x7faa995b0000+0xc0328) [0x7faa99670328]
(EE) 12: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7faa986b3000+0xfbd0) [0x7faa986c2bd0]
(EE) 13: (vdso) (0x7fff447c5000+0x70c) [0x7fff447c570c]
(EE) 14: (vdso) (__vdso_gettimeofday+0x161) [0x7fff447c5d01]
(EE) 15: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xf3a8e) [0x7faa928ffa8e]
(EE) 16: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x8007e) [0x7faa9288c07e]
(EE) 17: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xf7a0b) [0x7faa92903a0b]
(EE) 18: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xbb9e2) [0x7faa928c79e2]
(EE) 19: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x5580ec) [0x7faa92d640ec]
(EE) 20: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x52b819) [0x7faa92d37819]
(EE) 21: /usr/bin/X (BlockHandler+0x44) [0x7faa9960cb94]
(EE) 22: /usr/bin/X (WaitForSomething+0x114) [0x7faa9975d7f4]
(EE) 23: /usr/bin/X (0x7faa995b0000+0x58811) [0x7faa99608811]
(EE) 24: /usr/bin/X (0x7faa995b0000+0x4757a) [0x7faa995f757a]
(EE) 25: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7faa97300ea5]
(EE) 26: /usr/bin/X (0x7faa995b0000+0x478c1) [0x7faa995f78c1]
(EE) 
[xfixes] Barrier event queue full.  Dropping further events
(EE) BUG: triggered 'if (inSignalContext)'
(EE) BUG: ../../os/log.c:484 in LogVMessageVerb()
(EE) Warning: attempting to log data in a signal unsafe manner while in signal context.
Please update to check inSignalContext and/or use LogMessageVerbSigSafe() or ErrorFSigSafe().
The offending log format message is:
[xfixes] Barrier event queue full.  Dropping further events

(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7faa99760476]
(EE) 1: /usr/bin/X (LogVMessageVerb+0x195) [0x7faa9976b755]
(EE) 2: /usr/bin/X (ErrorF+0x8c) [0x7faa9976b98c]
(EE) 3: /usr/bin/X (0x7faa995b0000+0xebb4e) [0x7faa9969bb4e]
(EE) 4: /usr/bin/X (miPointerSetPosition+0x128) [0x7faa9974c218]
(EE) 5: /usr/bin/X (0x7faa995b0000+0x6cdec) [0x7faa9961cdec]
(EE) 6: /usr/bin/X (0x7faa995b0000+0x6dfc7) [0x7faa9961dfc7]
(EE) 7: /usr/bin/X (GetPointerEvents+0xe3) [0x7faa9961f503]
(EE) 8: /usr/bin/X (QueuePointerEvents+0x1d) [0x7faa9961f9ed]
(EE) 9: /usr/lib/xorg/modules/input/evdev_drv.so (0x7faa92175000+0x5f44) [0x7faa9217af44]
(EE) 10: /usr/bin/X (0x7faa995b0000+0x96927) [0x7faa99646927]
(EE) 11: /usr/bin/X (0x7faa995b0000+0xc0328) [0x7faa99670328]
(EE) 12: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7faa986b3000+0xfbd0) [0x7faa986c2bd0]
(EE) 13: (vdso) (0x7fff447c5000+0x70c) [0x7fff447c570c]
(EE) 14: (vdso) (__vdso_gettimeofday+0x161) [0x7fff447c5d01]
(EE) 15: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xf3a8e) [0x7faa928ffa8e]
(EE) 16: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x8007e) [0x7faa9288c07e]
(EE) 17: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xf7a0b) [0x7faa92903a0b]
(EE) 18: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0xbb9e2) [0x7faa928c79e2]
(EE) 19: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x5580ec) [0x7faa92d640ec]
(EE) 20: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so (0x7faa9280c000+0x52b819) [0x7faa92d37819]
(EE) 21: /usr/bin/X (BlockHandler+0x44) [0x7faa9960cb94]
(EE) 22: /usr/bin/X (WaitForSomething+0x114) [0x7faa9975d7f4]
(EE) 23: /usr/bin/X (0x7faa995b0000+0x58811) [0x7faa99608811]
(EE) 24: /usr/bin/X (0x7faa995b0000+0x4757a) [0x7faa995f757a]
(EE) 25: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7faa97300ea5]
(EE) 26: /usr/bin/X (0x7faa995b0000+0x478c1) [0x7faa995f78c1]
(EE) 
(WW) Warned 3 times about sigsafe logging. Will be quiet now.
[xfixes] Barrier event queue full.  Dropping further events
[xfixes] Barrier event queue full.  Dropping further events
[xfixes] Barrier event queue full.  Dropping further events
```

It just goes on from there. I've tried googling for quite awhile, all I'm finding is unfixed bug reports and what not.

---

### Post by FinalShot on 2013-05-07
Tried the open source driver and this still occured. I've still had no luck finding a solution with google.

---

### Post by FinalShot on 2013-05-08
Bump.

---

### Post by Sylslay on 2013-05-08
Hi same problem on Samsung R730 laptop - but did't test vlc and cpu use is low but, mouse get stock after 5 min from boot - abut 90% of all boots.
I can't get new bios becouse laptop is from 2010 and no support any more for new frimware.

I think that I have bad ram and I bought cheap 2 stick (and I will go with new config duall channel symetric instead asymentric)
, and meaby something with hdd - some times when shout down linux the head make noise and are hit ....

For me at the moment evrything looks like "memory leak" or some pin at hdd is broken and hdd works sometimes very slow????
than I replace ram than I will tested more. (when benchmarking hdd the results going from 90-40 MB/s - down all the time....)

Mobo is with  GPU intel  GM45  and Mobile 4 Series Chipset Integrated Graphics Controller.

Same problem under Fedora.
I roule out 32/64 bit version of OS (few boots from usb and sorted) same malfunction.

But under windows seam to be ok lage free on win 7 32bit (meaby not tested enugh - rearly used)


BTW: MY /etc/sysctl.conf TWEAKS:

# Decrease swap usage to a workable level
vm.swappiness=2

# Improve file/folder browsing speed
vm.vfs_cache_pressure=50

# Set maximum amount of memory allocated to shm to 256MB
kernel.shmmax = 268435456

# Disable power level Hdd
hdparm -B 255 /dev/sda
hdparm -c /dev/sda

Replaced 3GB ram with 4GB ram. It worsk 8.6% faster on Duall CHannel - symetric. :-)

HARDWARE ISSUE. YES BUT WHEN I REPLECED RAM FROM 3GB TO 4GB PROBLEM PRESIST.

I ADD THIS LINE TO GRUB.CFG AND UBUNTU 13.04 IS FLAYING NOW ALL THE TIME.
SOME ISSU WITH INTEL DRVIERS OR GRAPHIC !!!!!!!!!

PROBLEM SOLVED - AFTER LLLLLLLLLONG TIME. WITH
> set grub_gfxmode=1500x900x32

---

### Post by FinalShot on 2013-05-10
Bump.

---

### Post by FinalShot on 2013-05-11
Bump.

---

### Post by FinalShot on 2013-05-14
Bump.

---

### Post by anahorn on 2013-05-16
I have exactly the same problem with Ubuntu 13.04. The system dramatically slows down in 5 minutes after reboot. Then it keeps lagging for 30 sec - 1 min, hardly allowing to move the mouse pointer, it's almost frozen. This is a very annoying bug.

---

### Post by FinalShot on 2013-05-18
Bump. This is making linux unusable as whole, which sucks as it is my primay OS.

---

### Post by anahorn on 2013-05-22
I've submitted a bug to Launchpad: [https://bugs.launchpad.net/bugs/1182753](https://bugs.launchpad.net/bugs/1182753)

---

