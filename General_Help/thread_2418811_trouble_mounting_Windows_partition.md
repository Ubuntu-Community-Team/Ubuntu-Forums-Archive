---
title: "trouble mounting Windows partition"
date: 2019-05-11
forum: General Help
---

### Post by dora5 on 2019-05-11
I am trying to use Ubuntu booted from USB to view and rescue files on a hard drive that was accidentally fast/ quick formatted and the first partition partly written over with a new partition. 

I have successfully used testdisk to rescue the files from the other three partitions that were on the hard drive.   Testdisk can't make head or tail of the first partition on what remains of the first partition (which was physically much larger than the 10 GB partition that was created).  Specifically, it says it can't open it.   I don't want to spend several days imaging the entire drive and trying to pick what Ineed of unlabelled files if I can help it.

In Disks, Ubuntu shows the troubled disk, with the two partitions.   "Recovery Partition 1" 10 GB NTFS.  Partition 2 990 GB Unknown.  

Understand, in Windows, Testdisk tells me the format of the second partition is unknown or RAW, though it should be NTFS.   But then, it tells me the partitions whose data I have been rescuing are NTFS.   It tells me the size of the second partition with the files I can potentially rescue is 931 GB.

In Files, the Windows drives and their partitions on the computer display under Other Locations, more or less.   The troubled hard drive doesn't display at all, but all the other drives with Windows partitions and files on them arre there and I am able to click on them and examine the contents.   

Logically there exists a hard drive /dev/sdc that is not displaying, since /dev/sda, /dev/sdb, and /dev/sdd all show.  

fdisk lists /dev/sdc:  931.5 GiB, etc.  sectors of 1 * 512 = 512 bytes etc.   

/dev/sdc1  start 2048  end 20482047  secttors 20480000 size 9.8G  ID 7 Type HPFS/NTFS/exFAT
/dev/sdc2  start 20482048  end 1953521663  sectors 193303966   size 921.8G   ID 7  Type HPFSNTFS/exFAT

That's the drive I want to view and copy the files.   

I have tried a number of commands. 

I am in bash.   sudo /bin/bash
I made a directory to mount the partition.   mkdir /media/disk

mount -t ntfs-3g /dev/sdc2 /media/disk -o force

I got 
NTFS signature is missing
Failed to mount '/dev/sdc2':  Invalid argument.
The device '/dev/sdc2' doesn't seem to have a valid NTFS
Maybe the wrong device or the whole disk inst of a partition.

mount -t ntfs-3g /dev/sdc /media/disk -o force 
got the same error.

sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sdc2 /media/disk
same error

tried it again with ntfs-3g and got the same error.

I tried the command for if it's a FAT format.  

sudo mount -t vfat -o iocharset-utf8,umask=000 /dev/sdc2 /dev/disk
It can't find /dev/disk in /etc/fstab/

I tried creating /etc/fstab again and it said it already exists.   

I tried sudo mount /dev/sdc2 /media/disk -o force and got
mount: /media/disk:  wrong fs type, bad option, bad superblock on /dev/sdc2, missing codepage or helper program, or some other error.


It looks as if the trouble is that part of Ubuntu thinks the partition is formatted in NTFS, and part of it does not.    Windows sometimes thinks it's NTFS and sometimes thinks it's RAW.    Is there a way to mount a disk if you don't know what format it will recognize?    


I saw a hint online that I have to have ntfs-3g INSTALLED for it to work, and I may not since I'm running Ubuntu from a live USB.   I do have the option of installing Ubuntu to a hard drive that I had Ubuntu installed on on my old motherboard and processor which of course won't work now anyway - but someone would have to tell me how to install the package that contains it.   I have Ubuntu installed and running on a computer but haven't more than occasionally used it in a couple of years.

I also don't know exactly what ntfs-3g does, supposed to help with problems encountered using Ubuntu to rescue files from a Windows hard drive.

Online discussions of this problem have sometimes turned up the explanation that the drive was encrypted, but this one isn't.

I'd appreciate your help!

Yours,
Dora Smith

---

### Post by oldfred on 2019-05-11
Windows NTFS driver is now standard in Ubuntu.

Most times issue is that Windows 8 or 10 uses fast start up which also sets hibernation flag on every NTFS partition. And then the Linux NTFS driver will not mount the partition read/write to prevent damage. You may be able to mount read only.

Also NTFS partition must have an NTFS signature in the partition boot sector (BS or PBR). If not it may be shown as RAW or unformated. Many install grub mistakenly to PBR and damage the NTFS partition. Test disk often can restore a BS as NTFS has backup, or it can create a new BS using Rebuild BS. But that may still be the XP type, and new systems need the Windows 7, 8 or 10 type. You can fix that with chkdsk from a Windows repair flash drive.
[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

