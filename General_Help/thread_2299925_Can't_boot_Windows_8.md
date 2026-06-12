---
title: "Can't boot Windows 8"
date: 2015-10-22
forum: General Help
---

### Post by artemiy2 on 2015-10-22
Hi there,

I have laptop Lenovo with Windows 8 UEFI. I've install Ubuntu 15.04. After installing Ubunt, Windows 8 option in boot menu was disappeared.
I'm tried repair boot by Boot-Repair, but it didn't help.
Log here [http://paste.ubuntu.com/12894897/](http://paste.ubuntu.com/12894897/)

How can I repair my boot loader?

---

### Post by oldfred on 2015-10-22
Your are the third or fourth user with this issue. I was thinking it was user error installing grub to sda1 a NTFS partition, but now start to wonder if a major bug?
Did you ever before install grub to a partition?
Is this an upgrade?

This is the problem, Windows has essential boot info in the PBR - partition boot sector. And while grub can (but never recommended) be installed to a partition, it never should be installed to a NTFS partition.

```
 sda1: ______________________________________________________

       File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                       and looks at sector 1907595968 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


```

NTFS keeps a backup of its partition boot sector, and usually you can restore it easily with testdisk from a Ubuntu live installer or most Linux repairCDs. 

       Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Post this also, it may need to be reset to prevent issue from re-appearing on a major grub update. Only need the one line.
       
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short

Another thread, same issue:
[http://ubuntuforums.org/showthread.php?t=2299579](http://ubuntuforums.org/showthread.php?t=2299579)

---

