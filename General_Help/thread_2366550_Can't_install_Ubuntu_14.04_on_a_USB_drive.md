---
title: "Can't install Ubuntu 14.04 on a USB drive"
date: 2017-07-19
forum: General Help
---

### Post by alexwaltz on 2017-07-19
The hard drive on my PC has failed, but I have two external USB hard drives (500 GB and 1 TB).  I have downloaded Ubuntu 14.04 and burnt it to both a DVD and to a USB stick.  From there, I am trying to install it on the USB drive.  The build completes fine without any error message.

However at the end of the build, I take out the build media and reboot the PC.  On first boot up, I get the error message "error invalid arch-independent elf magic entering rescue mode"

I have formatted the drives, removed the partitions, performed wipes, etc.  The messages are always slightly different but something similar.

Any thoughts on why I'm getting this and how to fix it?

Thank you

---

### Post by johndough2 on 2017-07-19
Hi

Try It Knoppix which is Debian based like Ubuntu.  Also consider clonezilla.

You could try a version 17.04 of Ubuntu.  It may be the writer itself.

---

### Post by oldfred on 2017-07-19
Is install UEFI or BIOS?
Are you selecting to boot from USB drive?
Did grub get installed to external drive (only works directly if BIOS)?

Elf error is often wrong version of grub. Or you have old version of grub in MBR and new install updated into internal drive. Or you have UEFI and its BIOS or vice-versa.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Do not run Boot-Repair's auto fix, best if someone reviews report first. 
But if you do run anything run advanced mode, select correct install, and select MBR of same drive for full uninstall/reinstall of grub. Then make sure BIOS boots from that drive.

If UEFI manual copying of files to an ESP on external drive is required. And external must be gpt partitioned.

---

