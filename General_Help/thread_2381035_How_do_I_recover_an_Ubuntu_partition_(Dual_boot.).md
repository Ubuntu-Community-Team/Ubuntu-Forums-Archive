---
title: "How do I recover an Ubuntu partition? (Dual boot.)"
date: 2017-12-25
forum: General Help
---

### Post by Mugsy323 on 2017-12-25
I have/had 64bit Ubuntu 17.04 installed on a partition on my E: drive (SSD) in a Dual Boot configuration with 64bit Win7 on my C: drive, but I can no longer boot Ubuntu.

The other day, my Windows partition was hit by a nasty virus. I was able to recover it, but now Ubuntu won't boot. I used to launch Linux by selecting its partition from the BIOS Boot Menu (F12), which loaded GRUB, but now, when I try to boot the partition, I get the GRUB CLI telling me there is no Linux partition.

I booted using an Ubuntu LiveCD and launched "GParted". It is reporting my old partition as having "No Filesystem".

Is there a way to recover the partition (and Boot Menu) without destroying my data? Thanks.

---

### Post by TheFu on 2017-12-28
It is likely that Windows recovery wiped the grub install from the system.

Boot from an ubuntu liveCD (or flash drive with the same release of Ubuntu), then reinstall grub to the HDD.  That should find any existing Ubuntu install, any Windows installs, and setup grub to access both.  Reboot, pull the flash drive out and let grub show the options.  Both should work, in theory.

If that doesn't work, then you'll need to post lots and lots of data here so we can try to figure out if there is any chance of getting whatever you are missing back.  Generally, having a backup is the best answer.  Versioned backups solve 1001 problems.  As for posting all that data, the easiest way is to get boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  to make it. Follow that link and do what it says, then post the link it generates back here.

---

