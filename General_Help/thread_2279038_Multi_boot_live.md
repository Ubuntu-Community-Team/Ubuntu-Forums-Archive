---
title: "Multi boot live"
date: 2015-05-20
forum: General Help
---

### Post by FallenMass on 2015-05-20
I created two partitons on my flashdrive, sdb1 holds ubuntu live, sdb2 holds arch live. How would I go about installing grub to sdb so that I can choose what distro I want to boot from.  I can't seem to find any good tuts on this search brings up how to reinstall existing grub.

---

### Post by oldfred on 2015-05-20
I have all my ISO in one folder in various partitions on different flash drives or hard drives. Then my path is always the same and easier to debug. Correct path is often an issue. And with my system flash drive is not always the same. But with BIOS & grub the boot drive will always be hd0, so you have one install in hd0,1 and the other in hd0,2 and then whatever folder structure you have. I normally use /iso, or /boot/iso.

UEFI or BIOS boot?
I did get it to work with UEFI, but without having done it in BIOS for a while not sure I would have gotten it to work.

You just need to install grub to flash drive and manually create you own grub.cfg with correct paths to where ISO is.

       This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by FallenMass on 2015-05-20
Awesome that did the trick, Thank you

---

