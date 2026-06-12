---
title: "windows grub entrance does not work"
date: 2015-08-04
forum: General Help
---

### Post by pepe13 on 2015-08-04
I have used boot repair to create a report that is [here ]("http://paste.ubuntu.com/11998571/"), the point is that choosing to startup windows reloads grub again and again, so I'm unable to start windows Any sugestion?

---

### Post by grahammechanical on 2015-08-04
I can tell you this. As far as I can see Grub is looking in the right place for the Windows boot loader. The Grub configuration file (grub.cfg) is looking to set root='hdo,msdos1' And that = first hard drive and first partition or sda1. And that is where /bootmgr and /Boot/BCD are. Those two should be pointing in turn to sda2 /windows/System32/winload.exe to load Windows 7. It is this point that the process is breaking down, in my opinion.

Regards.

---

### Post by yancek on 2015-08-04
The problem is that you have apparently accidentally installed Grub to the windows partition (sda1) and you will need to reinstall windows boot code which I believe will also overwrite the Grub code in the MBR.  If you can do this with the installation media you have for windows, it would then be a simple matter of reinstalling Grub properly to boot both systems.  See the link below which explains the options for someone in the exact same situation.  You must have made an incorrect selection sometime as Grub is not going to install to a windows partition without user intervention.

[http://ubuntuforums.org/showthread.php?t=1702811](http://ubuntuforums.org/showthread.php?t=1702811)

---

### Post by pepe13 on 2015-08-04
> **yancek said:**
> The problem is that you have apparently accidentally installed Grub to the windows partition (sda1) and you will need to reinstall windows boot code which I believe will also overwrite the Grub code in the MBR.  If you can do this with the installation media you have for windows, it would then be a simple matter of reinstalling Grub properly to boot both systems.  See the link below which explains the options for someone in the exact same situation.  You must have made an incorrect selection sometime as Grub is not going to install to a windows partition without user intervention.

[http://ubuntuforums.org/showthread.php?t=1702811](http://ubuntuforums.org/showthread.php?t=1702811)

you´re right sherlock holmes :p

I realized after my first post that in a first installation I installed grub into sda1 instead of sda, and of course windows have lost it´s boot code, wich it is fixed with the original w7 dvd.

could you please tell how have you reached to this?

anyway, thank you all.

---

### Post by Mark Phelps on 2015-08-04
> could you please tell how have you reached to this?

Simple: the boot repair report shows Grub2 present in the sda1 ntfs partition.

---

### Post by oldfred on 2015-08-04
Did Windows fixes work?

Sometimes with grub in the partition boot sector, Windows does not even recognize the partition as one it should repair. It just does not see it as NTFS. You then need to use testdisk to either repair it or at least make it NTFS, but testdisk's version of NTFS is the old XP. But then at least Windows will see it and let you repair it.

       As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

### Post by pepe13 on 2015-08-04
thank you once again

---

### Post by pepe13 on 2015-08-04
> **oldfred said:**
> Did Windows fixes work?

Sometimes with grub in the partition boot sector, Windows does not even recognize the partition as one it should repair. It just does not see it as NTFS. You then need to use testdisk to either repair it or at least make it NTFS, but testdisk's version of NTFS is the old XP. But then at least Windows will see it and let you repair it.

       As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)


worked for me following this directions

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

tahnk you

---

