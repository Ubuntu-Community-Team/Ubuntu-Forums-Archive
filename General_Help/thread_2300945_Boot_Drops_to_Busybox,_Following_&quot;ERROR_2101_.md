---
title: "Boot Drops to Busybox, Following &quot;ERROR 2101 Mini SSD Detect failure&quot;, Unstable Boot"
date: 2015-10-29
forum: General Help
---

### Post by Jollyhrothgar on 2015-10-29
Hello,

I'm running a Thinkpad W530, with Ubuntu 14.04 LTS installed as the only operating system. I've recently made the switch from Windows 10 to ubuntu. This laptop came with a microSSD cache drive. I eventually bought a samsung 840 SSD as a replacement for my slow primary hard drive, and installed ubuntu on it.  Everything was going great until I did four things, around the same time, and I'm not sure which one of them broke everything, but I suspect it was after I attempted, and failed to partition my micro SSD on /dev/sdb using gParted. I didn't touch /dev/sda where my primary OS partitions are. The four things I did which proceeded my issue are:

[LIST]
[*]installed TLP power management
[*]installed cinnamon desktop environment
[*]attempted to partition my cache ssd, partitioning failed with input/output errors, problems started
[*]uninstalled cinnamon desktop environment
[/LIST]

My issue is:

On reboot, I get a system-beep from my laptop, and a message "Error 2101 Detection error on HDD2 (mini sata)". I am then dropped to BusyBox, where I receive some more errors, but they don't seem to be consistent. When I exit busybox, I can actually boot into Ubuntu. In case there was a problem with my primary boot partition (if I'm using the correct language, apologies if not), I ran a boot repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and the log from this can be read here: [http://paste.ubuntu.com/13001040/](http://paste.ubuntu.com/13001040/)

Ideally, I'd like to use my mini SSD, but its only 16 gigabytes, so its not a huge loss if I can't. I'd just like to be able to restart and shut down my computer. Thanks for reading, and your help.

EDIT:

Okay, after several more hours of searching the web, it seems as though the cache drive can be corrupted, unseated, or a variety of other things which make it undetectable, or partially detectable at the hardware level. I believe I had a faulty Micro SATA chip, which was the source of my problems. I removed the drive performing a bit of laptop surgery, and now everything is fine. Cheers!

---

