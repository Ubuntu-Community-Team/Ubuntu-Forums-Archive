---
title: "Partition problem with rescued disk"
date: 2015-03-29
forum: General Help
---

### Post by murboy on 2015-03-29
First off, I'm new to Ubuntu, so very possible confusion on my part.

I've managed to rescue a failing disk from a Windows 7 laptop using gnu ddrescue and copying to an image file. The disk has 4 partitions: 3 ntfs and 1 fat. I was able to mount each of the partitions, using the image file and the appropriate offsets. I could view the files on each. I then used ddrescue to copy the image file to a new disk to create a bootable system. I've attached the disk (USB drive) to both the Ubuntu system and another Win 7 laptop. On Win7 the first 2 partitions are accessible and useable, but the last 2 are labeled Raw. On Ubuntu, the first 2 partitions are mounted automatically. When I try to mount the 3rd partition (sdb3), the error says "NTFS signature is missing". I've tried mounting the 3rd partition using /dev/sdb with the appropriate offset option and get the same error. I can still mount the original image file with the same command successfully.

Thanks in advance for any suggestions.

Ed

---

### Post by murboy on 2015-03-29
One other relevant note: "sudo fdisk -l /dev/sdb" shows the 4 partitions with the correct file systems for each.

---

### Post by oldfred on 2015-03-29
All NTFS partitions have a partition boot sector or PBR or BS similar to a MBR in structure. It has additional boot info even if not a boot partition, but must also have the correct start & size of the NTFS partition that matched the partition table.

Not sure if from a recovery if the backup is still there. NTFS does keep a backup which you can restore if it also is not damaged. You can install testdisk into Ubuntu or Ubuntu live installer.
       As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

If the backup BS is also damaged or missing. You need a Windows repair console.
Bootsect.exe updates the master boot code (BS) for hard disk partitions
You can use this tool to restore the Boot_Sector (BS) on your computer.

        Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

---

