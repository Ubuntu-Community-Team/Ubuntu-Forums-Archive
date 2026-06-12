---
title: "Nasty system lock-up"
date: 2014-07-21
forum: General Help
---

### Post by mayagrafix on 2014-07-21
My ubuntu OS is suffering from a nasty bug that locks up (keyboard and mouse freeze) and produces a similar screen to this (sometimes) after while:
> [ 3933.364188] mce: [Hardware Error]: CPU 0: Machine Check Exception: 4 Bank 3: fe00000000200135

[ 3933.364191] mce: [Hardware Error]: TSC a0255fbd7f0 ADDR 42dd14480 MISC d62285

[ 3933.364194] mce: [Hardware Error]: PROCESSOR 0:306a9 TIME 1398357146 SOCKET 0 APIC 0 microcode 15

[ 3933.364195] mce: [Hardware Error]: Run the above through 'mcelog --ascii'

[ 3933.364196] mce: [Hardware Error]: Machine check: Processor context corrupt
I copied this one from another forum so the numbers are different but the idea is the same. In the other forum the consensus was that this was caused by a PSU problem, however when I boot the PC with Windows OS, the problem does not repeat. I have been running windows for the last 7 days and all AoK. As soon as I boot with Ubuntu, the PC will freeze and I will have to do a hard reboot.

---

### Post by mayagrafix on 2014-07-23
nobody knows anything about the aforementioned error?

---

### Post by sp40140 on 2014-07-23
What are your hardware specs? what version of ubuntu is installed? what kernel version? Is this new install? Have you ever had ubuntu working without issue on this machine? What version of windows are you running?

---

### Post by tgalati4 on 2014-07-23
Make a 12.04 USB stick and boot from that and see how long it stays up.  A simpler test is to boot from an earlier kernel on your system.  Hit esc during the boot to get to the grub2 menu and select an older kernel.  Boot from rescue mode only to see if you can separate the kernel from the desktop environment.

Unfortunately, this type of problem will require some specific troubleshooting to isolate the problem.  Did you perform any updates recently?

---

### Post by mayagrafix on 2014-07-27
Thanks for advice on booting with earlier kernel. After more testing, I found a bios setting that was causing the problem (Enable On Board LAN). So far so good  last 24 hrs.

---

