---
title: "Unable to select USB in boot menu"
date: 2017-10-28
forum: General Help
---

### Post by KenUBF on 2017-10-28
Hi all! I'm having issues getting my ASUS E200HA laptop to boot from a Ubuntu MATE 17.10 USB, created with the Ubuntu Disk Creator. It boots fine on my other computer so it must have something to do with my laptop. The USB is seen with Disks utility and lsusb. But it just will not show up in the BIOS, nor boot menu. In the Disk utility I selected the drive to boot immediately after reboot but that didn't work either. I'm somewhat new with booting from USB's and am stuck. I've had no issues like this in the past. It seems to have just started after upgrading to Ubuntu 17.10. Thanks for any help you can give.

---

### Post by TheFu on 2017-10-28
Not all USB disks are compatible with all USB ports.
* try a different port
* try a different flash drive
Some computers only boot in uefi mode.
Some computers only boot in "legacy" MSDOS mode.
Some computers (really old ones) cannot boot from USB at all.

If 17.10 is an issue, go back to 16.04.  Hopefully, you made a backup before starting all this.  That is what I would do.

---

### Post by KenUBF on 2017-12-01
Thank you for the reply TheFu. I'm not sure what happened, but I tried again a week or so later and it worked so I installed Ubuntu MATE 16.04 and everything is working great now.

---

