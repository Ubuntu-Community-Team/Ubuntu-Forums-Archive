---
title: "Boot issues in Ubuntu 6.10"
date: 2007-04-17
forum: General Help
---

### Post by darkwarrior on 2007-04-17
[SIZE="3"][SIZE="4"]HI  new to linux , i have a boot problem, downloaded , and burnt the ubuntu 6.10 to cd , install went perfectly (It seems) and then after rebooting the 'grub' loaded and gave me a error 18 not sure what this is, the machine is a Pentium 3 , 256MB Ram a biostar bios, a compaq 18gig scsi HD a 52x cdrom, adaptec 2940 ultra wide scsi card, i erased the drive prior to installation and had ubuntu auto partition the drive, i have reinstalled it but to no avail same error message comes up any help would be greatly appreciated....[/SIZE][/SIZE]

---

### Post by Zwalther on 2007-04-17
Your disk is probably too large for your bios. Usually the easiest thing is to move you boot partition to the front of the disk, but that means you'll have to reinstall.

A search for 'grub error 18' on google gave me this:

Grub error 18

info grub schreef:
18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range). 

(From: [http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656) )

---

