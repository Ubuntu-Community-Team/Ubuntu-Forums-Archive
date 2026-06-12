---
title: "Grub- Dual boot problem"
date: 2007-06-30
forum: General Help
---

### Post by Linkerator on 2007-06-30
My friend and I installed Ubuntu on one of the hard drives on our PC, the master drive. Windows XP is on the slave drive. When Grub boots up, it gives out an error 21, "The disk is not found". Ubuntu recognizes the disk. I think the problem is that Grub is set to check the master (hda) for Windows XP instead of hdb. How can I change the MBR to look in hdb to boot Windows XP?

---

### Post by confused57 on 2007-06-30
> **Linkerator said:**
> My friend and I installed Ubuntu on one of the hard drives on our PC, the master drive. Windows XP is on the slave drive. When Grub boots up, it gives out an error 21, "The disk is not found". Ubuntu recognizes the disk. I think the problem is that Grub is set to check the master (hda) for Windows XP instead of hdb. How can I change the MBR to look in hdb to boot Windows XP?
You might want to enter your bios setup & make sure the slave drive controller is set to "auto"...if this doesn't work, then maybe check your jumper settings.

---

### Post by Linkerator on 2007-07-01
> **confused57 said:**
> You might want to enter your bios setup & make sure the slave drive controller is set to "auto"...if this doesn't work, then maybe check your jumper settings.

It's set to auto, and there are no jumper problems, both are set to Cable Select. I think it is more for a Grub problem than a BIOS/jumper problem.

---

### Post by confused57 on 2007-07-01
Here are some possible solutions for grub error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

You might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD may be able to boot your Window's drive.

---

