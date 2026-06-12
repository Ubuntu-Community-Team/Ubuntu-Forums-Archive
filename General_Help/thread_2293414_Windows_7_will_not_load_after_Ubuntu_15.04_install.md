---
title: "Windows 7 will not load after Ubuntu 15.04 install"
date: 2015-09-04
forum: General Help
---

### Post by Chuck_Long on 2015-09-04
Hi, I'm a total Ubuntu noob, and I tried to install Ubuntu next to my Windows 7 for a dual boot machine. Ubuntu works perfectly, but Windows will not load. When I start my machine, I get a screen with about 4 options: Ubuntu, Ubuntu advanced options Memtest and Windows 7. When I select Windows and hit enter, nothing happens. 

What did I break, lol?

---

### Post by oldfred on 2015-09-04
Need details:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Chuck_Long on 2015-09-05
Thanks! Here's a link to the report:

[http://paste.ubuntu.com/12290315/](http://paste.ubuntu.com/12290315/)

---

### Post by oldfred on 2015-09-05
You have a Windows boot loader in the MBR and grub installed to the PBR or partition boot sector of Windows NTFS boot partition.
Windows has essential boot files in the PBR. You can never install grub to a NTFS partition.

Install grub to MBR so Ubuntu can boot. 
NTFS PBR has a backup. Testdisk can easily restore from the backup if the backup is valid.
Testdisk may say PBR is valid as you can have grub in a partition, just not in NTFS partitions.

       [http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by Chuck_Long on 2015-09-05
Thanks for your help. I'll work on this tomorrow and let you know how it goes.

---

