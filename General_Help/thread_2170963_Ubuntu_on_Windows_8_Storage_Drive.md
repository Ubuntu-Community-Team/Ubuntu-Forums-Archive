---
title: "Ubuntu on Windows 8 Storage Drive"
date: 2013-08-28
forum: General Help
---

### Post by b.pellegrini on 2013-08-28
I'm fairly new to the world of Linux.  I played around with Ubuntu and Debian for a while, but never really got into using them.  I'm wanting to install Ubuntu alongside my windows 8 storage drive.  Is this going to erase my drive?  I've got Windows 8 on a SSD and most of my data on a second internal drive.  Will installing Ubuntu wipe my second drive when I partition part of it to FAT32?  Would it be easier to install on the SSD with Windows and just create a partition for data on the second drive rather than a partition for the OS?

Thanks in advance

---

### Post by Impavidus on 2013-08-28
> **b.pellegrini said:**
> I'm fairly new to the world of Linux.  I played around with Ubuntu and Debian for a while, but never really got into using them.  I'm wanting to install Ubuntu alongside my windows 8 storage drive.  Is this going to erase my drive?  I've got Windows 8 on a SSD and most of my data on a second internal drive.  Will installing Ubuntu wipe my second drive when I partition part of it to FAT32?  Would it be easier to install on the SSD with Windows and just create a partition for data on the second drive rather than a partition for the OS?

Thanks in advance

Not necessarily. If you install Ubuntu alongside Win8 your Win8 including all files should remain intact, but an error is easely made. Therefore make backups nonetheless. The basic idea is that you use windows tools to create unallocated disk space, then boot an Ubuntu live disk and use that to create Linux partitions and install. It may be a good idea to browse the documentation at [https://help.ubuntu.com](https://help.ubuntu.com)

There are some tricky parts with Win8 (UEFI, secure boot, fast boot) that you should read about, but I'm not the specialist on that.

---

### Post by lah7 on 2013-08-28
On Windows, you can use the **Disk Management **tool (by right clicking Computer --> Manage) which allows you to shrink the partition to make room for an Ubuntu installation (the only limit here is how fragmented the drive is. Since you're on an SSD, I wouldn't have thought this is much of a problem.)

Then you can boot the Live CD and install Ubuntu alongside Windows, and it'll identify an empty partition and do the rest for you. :)

**However**, on modern PCs, your OEM may have tied Windows 8 to your system, like Impavidus had stated. You'll need to check your BIOS/UEFI settings and disable secure/fast boot. It's explained here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Once it's installed, a bootloader called GRUB will present you with the option to load Ubuntu or Windows 8.

---

### Post by oldfred on 2013-08-28
To dual boot both systems must be installed in the same boot mode UEFI or BIOS. So if Windows is UEFI, you really need to isntall Ubuntu in UEFI boot mode. Or if Windows is BIOS then Ubuntu needs to be installed in BIOS boot mode. Procedures are different depending which way you will boot Ubuntu.

Post this from terminal in Ubuntu live installer. 

sudo parted -l

---

