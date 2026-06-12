---
title: "System Randomly Slows to a Crawl"
date: 2013-05-21
forum: General Help
---

### Post by pennstatebadboy on 2013-05-21
I have a mysterious and annoying phenomenon happening to my system.

**Since I upgraded to 13.04, the following has been happening:**
Randomly -- usually once or twice a day -- my system will suddenly slow down to a point where it's unusable. It feels as if something has taken over the CPU. It's a docked laptop, so I can hear the fan when the CPU is taxed, and when this phenomenon happens, the fan spins like crazy.

When I say slow, I mean that the animations go into super-slow-motion; Lag time between clicks (switching windows, e.g.) is a few seconds; There's a delay between keystrokes and when the characters appear on screen. Everything runs slowly.

When I open the System Monitor and sort by CPU usage in the Processes tab, I don't see anything using more than 10 percent of the CPU. However, the "CPU History" graph in the "Resources" tab shows all 4 cores at very high levels.

I have tried to kill processes one-by-one, but nothing seems to do the trick. The only thing that works is logging-out or rebooting.

My question is: **How do I figure out what is making my system slow down?**

---

### Post by zero2xiii on 2013-05-21
Hay,

Try running in a terminal htop:

```
sudo apt-get install htop
htop
```

It is way better than any GUI app (so I hear, but it does show a LOT more information, even a proses path.

Cherz

---

### Post by pennstatebadboy on 2013-05-22
Htop found the culprit:
/usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nmolisten tcp vt7 -novtswitch

My understanding is that lightdm is the system graphics server, which should always be running.

But, why does it suddenly and randomly start using a crippling amount of CPU resources?

---

### Post by HiImTye on 2013-05-22
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
lightdm is ghe interactive login manager and shouldn't use any cpu if you're not using it, sounds like something that needs more investigation. you might want to file a bug report

---

### Post by pennstatebadboy on 2013-05-23
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
lightdm is ghe interactive login manager and shouldn't use any cpu if you're not using it, sounds like something that needs more investigation. you might want to file a bug report

I've researched a bit more and I think the command is referenced as "lightdm" because it's the first of many processes started by the X Server.

I'm not sure how to debug this. Is there a log that I can look at?

---

### Post by pennstatebadboy on 2013-06-05
I'm still troubleshooting this issue. My Xorg.0.log indicates that the GPU is hanging.

Anyone know a fix for this?


> (EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3615da5476]
(EE) 1: /usr/bin/X (mieqEnqueue+0x26b) [0x7f3615d8678b]
(EE) 2: /usr/bin/X (0x7f3615bf5000+0x6d472) [0x7f3615c62472]
(EE) 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f360ff58000+0x5f44) [0x7f360ff5df44]
(EE) 4: /usr/bin/X (0x7f3615bf5000+0x96927) [0x7f3615c8b927]
(EE) 5: /usr/bin/X (0x7f3615bf5000+0xc0328) [0x7f3615cb5328]
(EE) 6: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f3614cf8000+0xfbd0) [0x7f3614d07bd0]
(EE) 7: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3613a15747]
(EE) 8: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f3614af0338]
(EE) 9: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f3612497000+0x39010) [0x7f36124d0010]
(EE) 10: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f3612497000+0x3a1f7) [0x7f36124d11f7]
(EE) 11: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f3612497000+0x60d51) [0x7f36124f7d51]
(EE) 12: /usr/bin/X (BlockHandler+0x44) [0x7f3615c51b94]
(EE) 13: /usr/bin/X (WaitForSomething+0x114) [0x7f3615da27f4]
(EE) 14: /usr/bin/X (0x7f3615bf5000+0x58811) [0x7f3615c4d811]
(EE) 15: /usr/bin/X (0x7f3615bf5000+0x4757a) [0x7f3615c3c57a]
(EE) 16: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f3613945ea5]
(EE) 17: /usr/bin/X (0x7f3615bf5000+0x478c1) [0x7f3615c3c8c1]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
(EE) [mi] EQ overflow continuing.  100 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f3615da5476]
(EE) 1: /usr/bin/X (0x7f3615bf5000+0x6d472) [0x7f3615c62472]
(EE) 2: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f360ff58000+0x5f44) [0x7f360ff5df44]
(EE) 3: /usr/bin/X (0x7f3615bf5000+0x96927) [0x7f3615c8b927]
(EE) 4: /usr/bin/X (0x7f3615bf5000+0xc0328) [0x7f3615cb5328]
(EE) 5: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f3614cf8000+0xfbd0) [0x7f3614d07bd0]
(EE) 6: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f3613a15747]
(EE) 7: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f3614af0338]
(EE) 8: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f3612497000+0x39010) [0x7f36124d0010]
(EE) 9: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f3612497000+0x3a1f7) [0x7f36124d11f7]
(EE) 10: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f3612497000+0x60d51) [0x7f36124f7d51]
(EE) 11: /usr/bin/X (BlockHandler+0x44) [0x7f3615c51b94]
(EE) 12: /usr/bin/X (WaitForSomething+0x114) [0x7f3615da27f4]
(EE) 13: /usr/bin/X (0x7f3615bf5000+0x58811) [0x7f3615c4d811]
(EE) 14: /usr/bin/X (0x7f3615bf5000+0x4757a) [0x7f3615c3c57a]
(EE) 15: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f3613945ea5]
(EE) 16: /usr/bin/X (0x7f3615bf5000+0x478c1) [0x7f3615c3c8c1]
(EE) 
[ 34224.810] (EE) intel(0): Detected a hung GPU, disabling acceleration.
[ 34224.810] (EE) intel(0): When reporting this, please include i915_error_state from debugfs and the full dmesg.
[ 34224.810] [mi] Increasing EQ size to 512 to prevent dropped events.
[ 34224.811] [mi] EQ processing has resumed after 109 dropped events.
[ 34224.811] [mi] This may be caused my a misbehaving driver monopolizing the server's resources.


---

### Post by pennstatebadboy on 2013-06-14
I think I found the problem. It's a bug with Intel's SNA acceleration.

If anyone else is having this or a similar issue, you might be able to solve it by changing/creating your xorg.conf file following these instructions:
[http://askubuntu.com/questions/292224/ubuntu-13-04-bad-3d-performance-of-intel-ironlake](http://askubuntu.com/questions/292224/ubuntu-13-04-bad-3d-performance-of-intel-ironlake)

---

