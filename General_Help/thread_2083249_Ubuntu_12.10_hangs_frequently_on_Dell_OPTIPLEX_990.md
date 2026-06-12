---
title: "Ubuntu 12.10 hangs frequently on Dell OPTIPLEX 990 workstation"
date: 2012-11-11
forum: General Help
---

### Post by vksingh on 2012-11-11
Hi All,

I am using Ubuntu 12.10 desktop edition on Dell OPTIPLEX 990 workstation. The Ubuntu hangs frequently and I have to do hard reboot every time it hangs. I have installed the Ubuntu about 1 week back.

Any workaround to fix this issue, then please let me know.

Regards,
Vivek

---

### Post by lykwydchykyn on 2012-11-11
Hard lock-ups like that are almost always caused by:

 - hardware problems.
 - Driver problems.

Since your 990 is probably pretty new, let's assume it's not a hardware problem. Chances are it's a driver problem of some sort, most likely (but not for certain) a problem with the video card.

Next time it locks up, note the time.  After you reboot, open /var/log/kern.log and look for messages around the time that it locked up.  If it starts after the lock-up, check /var/log/kern.log.1.

If you find something that looks like a crash or says "kernel panic", post it up here.  If you're not sure, just post the log messages for about a minute before and after the time of the crash.

---

### Post by vksingh on 2012-11-14
[B]Nov 15 12:37:58 viveks kernel: [96778.079741] [drm] nouveau 0000:01:00.0: PGRAPH - TRAP
Nov 15 12:37:58 viveks kernel: [96778.079746] [drm] nouveau 0000:01:00.0: PGRAPH - ch 4 (0x0001850000) subc 3 class 0x8597 mthd 0x0f04 data 0x00000000
Nov 15 12:37:59 viveks kernel: [96778.245187] [drm] nouveau 0000:01:00.0: PGRAPH_TRAP_MP_EXEC - TP 1 MP 0: TIMEOUT at 07fe70 warp 18, opcode c0890205 00000780
Nov 15 12:37:59 viveks kernel: [96778.245200] [drm] nouveau 0000:01:00.0: PGRAPH_TRAP_MP_EXEC - TP 1 MP 1: TIMEOUT at 07fe70 warp 20, opcode c0890205 00000780
Nov 15 12:37:59 viveks kernel: [96778.245210] [drm] nouveau 0000:01:00.0: PGRAPH_TRAP_MP_EXEC - TP 1 MP 2: TIMEOUT at 07fe70 warp 16, opcode c0890205 00000780
Nov 15 12:37:59 viveks kernel: [96778.245216] [drm] nouveau 0000:01:00.0: PGRAPH - TRAP
[/B]
The above log was coming before reboot. Any idea what could be the reason?

Regards,
Vivek

---

### Post by lykwydchykyn on 2012-11-15
All those errors are coming from the nouveau driver, which is the default (open source) NVidia driver.  You could always try the proprietary Nvidia driver and see if that improves matters.  I believe the driver installation tool is hiding in the "software sources" tool these days.

---

### Post by Randymanme on 2013-02-23
BUMP

I'm having the same problem.  The computer that I'm using is the one in my signature, below.  It has an integrated Nvidia graphics card (Geforce 6150SE nForce 430).  

/var/log/kern.log

Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637796] Raw EDID:
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637802]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637803]      00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637804]      00 00 00 1f ff ff ff ff ff ff ff ff ff ff ff ff
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637805]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637806]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637808]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637809]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.637810]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Feb 23 10:32:30 randalls-EL1358G kernel: [ 1099.638949] [drm] nouveau 0000:00:0d.0: DDC responded, but no EDID for VGA-1

I've tried all the drivers listed in the additional drivers tab in repositories (and another one not there), and so far it looks like the Nouveau driver works the best.

At the time that I bought this computer, I didn't know that it's power supply (200 watts) won't support an after-market graphics card.  Has anyone any suggestions?

Any help would be much appreciated.  

Thanks

---

