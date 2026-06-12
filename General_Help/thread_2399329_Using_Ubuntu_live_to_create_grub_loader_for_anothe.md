---
title: "Using Ubuntu live to create grub loader for another OS."
date: 2018-08-24
forum: General Help
---

### Post by kennchee92 on 2018-08-24
Hi,

Here is my current situation, i have an IDE 80GB drive. That has turbolinux running on it, last few days it stopped working, and starts showing kernel panic errors "03:02". I took the drive out, "since the system was too old, that it doesn't support bootable usb", and hook it up to another PC. Ran Ubuntu 18.04.1 LTS live, repaired the drive with fsck. But after repaired the drive, the OS doesn't boot up, so another error pop out. "No Signature in boot partition". So i tried to use Ubuntu live to install grub but i am not very knowledgable with Linux. Fyi, previous OS was running Lilo, i tried to repair it, but it has issue as well.

So if someone could guide me on where and how to get the grub bootloader to be installed on that drive, i would be grateful.

---

### Post by yancek on 2018-08-24
Exactly how did you install Grub on the drive?  The link below is to the Ubuntu documentation on doing this.  Section 2.2 on that page discusses Fixing Grub.  You might try downloading Boot Repair and running it and using the Create BootInfo Summary option and posting a link to the output here.  Do not try to do repairs, just post the link and someone here may be able to suggest a fix.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by 1clue on 2018-08-24
While the Ubuntu disk is probably fine, I use [http://www.system-rescue-cd.org/](http://www.system-rescue-cd.org/) because it's not trying to demonstrate Linux or install it, it only focuses on booting and repairing an install of whatever you're running.

I always have a copy of it both on dvd and on a stick, just in case. I actually use it to install Linux instead of the installer cd.

---

### Post by C.S.Cameron on 2018-08-24
I use **mkusb** as a base for portable installs that work with BIOS and UEFI.

**Mkusb** makes a drive with FAT32 Boot partition, ISO9660 OS partition, ext2 Persistence partition and NTFS Windows/Linux data partition.

I replace the OS and Persistence partitions with a ext4 partition, then install Ubuntu on it using something else.

Select the new partition for the bootloader.

After install replace grub.cfg in the boot partition with the one from the OS partition, or write your own menuentries.

---

