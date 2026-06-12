---
title: "Unable to install Grub"
date: 2008-02-13
forum: General Help
---

### Post by miqie on 2008-02-13
I have two hardrives, master and slave.  I had Gutsy iinstalled on the slave with windows XP on the master.  The system booted fine with the grub menu giving me the option to boot either to XP or Ubuntu.    Due to being unable to resolve some problems getting an external USB drive to mount, I decided to reinstall Ubuntu, thinking that maybe a reinstall would help. I wiped the slave drive completely and reinstalled.   At 94% of the reinstall, I got the error message that the Grub install on (HD0) failed and this is a fatal error.  (HD0) is the disk that XP is on.  This is the where Grub was installed before,  successfully.  How can I resolve this problem.  I really would like to get Ubuntu back.

---

### Post by ajmorris on 2008-02-13
> **miqie said:**
> I have two hardrives, master and slave.  I had Gutsy iinstalled on the slave with windows XP on the master.  The system booted fine with the grub menu giving me the option to boot either to XP or Ubuntu.    Due to being unable to resolve some problems getting an external USB drive to mount, I decided to reinstall Ubuntu, thinking that maybe a reinstall would help. I wiped the slave drive completely and reinstalled.   At 94% of the reinstall, I got the error message that the Grub install on (HD0) failed and this is a fatal error.  (HD0) is the disk that XP is on.  This is the where Grub was installed before,  successfully.  How can I resolve this problem.  I really would like to get Ubuntu back.

Hi there,
hd0 is actually not the partition that windows is on. hd0 is the MBR (Master Boot Record), if windows is on the first partition, then it is on hd0,0 :)

Is ubuntu installed? or did upon getting to 94%, the install just die, and not complete?
if so, i suggest rebooting into the live cd, and checking in a Terminal, the output of ```
sudo fdisk -l
```
and checking if the partitions are correct.

Also, you could try installing grub to the MBR with the live cd first, before installing ubuntu itself.

AJ

---

### Post by miqie on 2008-02-13
The install died at 94% after giving me the grub install error.  Here is the output of fdisk -l.  WinXP is on hda  and I was installing Ubuntu on Hdb.  Also you mentioned "Also, you could try installing grub to the MBR with the live cd first, before installing ubuntu itself."  How do I do that?  I mean as far as what commands to issue in the terminal window.  I am very new at this.  


Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10e510e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1944    15615148+   c  W95 FAT32 (LBA)
/dev/hda2            1945        7476    44435790    f  W95 Ext'd (LBA)
/dev/hda5            1945        7476    44435758+   b  W95 FAT32

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x729cb918

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         609     4891761    c  W95 FAT32 (LBA)
/dev/hdb2            2402        2498      779152+  82  Linux swap / Solaris
/dev/hdb3             610        2401    14394240    b  W95 FAT32

---

### Post by miqie on 2008-02-13
Any ideas on this problem?

---

### Post by ajmorris on 2008-02-14
> **miqie said:**
> The install died at 94% after giving me the grub install error.  Here is the output of fdisk -l.  WinXP is on hda  and I was installing Ubuntu on Hdb.  Also you mentioned "Also, you could try installing grub to the MBR with the live cd first, before installing ubuntu itself."  How do I do that?  I mean as far as what commands to issue in the terminal window.  I am very new at this.  


To install grub to the MBR first before you install ubuntu itself, grub has to be installed to the partition.

then, you go into a terminal, and type:
```
1) grub
2) find /boot/grub/stage1
3) root (hd#,#) (the #s represent the numbers giving by step 2)
4) setup (hd0)
5) quit
6) reboot
```
(after the reboot, grub is installed) then you can try to install ubuntu itself.

have you tried the install again since you got the error?
and what type of install are you doing? i.e, from a live cd, or the alternative cd?

---

