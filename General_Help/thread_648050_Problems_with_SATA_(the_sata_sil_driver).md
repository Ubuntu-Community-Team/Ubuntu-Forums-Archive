---
title: "Problems with SATA (the sata_sil driver)"
date: 2007-12-23
forum: General Help
---

### Post by subxero on 2007-12-23
I recently added two new SATA hard drives to my computer (400 GB Western Digital drives) for a total of four drives - my original two drives are PATA. I use both Windows and Linux (Ubuntu 7.10), and upon booting into Linux after installing these drives, everything works fine for about 1-2 minutes and then the system locks up completely; the mouse cursor moves, but the system won't switch to a terminal, or restart X, or anything. Using the magic SysRq option I can reboot my system gracefully but I can't seem to get around the locking-up problem.

The drives are set up in RAID0 fashion (hardware-based RAID), for a total of 800 GB (I have no idea what I'm going to do with 800 GB of space, plus the 2x200 GB of my original two drives) and I'm concerned this may be causing my problem. Also, I haven't gotten around to reinstalling Windows and Linux yet, and as such, both of these drives are unformatted.

Booting into Recovery mode and editing /etc/modprobe.d/blacklist to include the "sata_sil" module solves my problem, but my drives are no longer accessible, so I'm pretty sure that the sata_sil module, the drives, or the configuration is at fault. What is weird, however, is that even with that module on the blacklist, its entry still appears in 'lsmod' and it is still loaded/consuming memory.

lspci tells me the chip is a "Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)". However, my motherboard documentation states it is a 3112. My motherboard documentation is also known to be wrong, so I wouldn't trust it completely.

Any ideas? If you need more info, ask :)

---

