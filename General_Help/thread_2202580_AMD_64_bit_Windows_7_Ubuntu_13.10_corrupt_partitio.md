---
title: "AMD 64 bit Windows 7 Ubuntu 13.10 corrupt partition"
date: 2014-01-29
forum: General Help
---

### Post by EnriqueFabuloso on 2014-01-29
Hello all,

I have a dual boot with AMD 64 bit. I have three partitions:

Ubuntu OS
Win 7 OS
Storage (I can share files between the two operating systems with this partition)

I can boot into both but 'Storage' is not mounting and apparently the partition table is corrupted.

I've looked at gparted, ntfsprogs, clonzilla on live cd etc. but the info for recovering seems deprecated.

Clonzilla told me I have an input/output error.

This looked promising but it didn't help:
[http://linuxexpresso.wordpress.com/2011/09/20/howto-fix-an-ntfs-partition-in-ubuntu/](http://linuxexpresso.wordpress.com/2011/09/20/howto-fix-an-ntfs-partition-in-ubuntu/)

I can provide screenshots log files whatever it takes. This partition has all my documents because I didn't want to slow down the partitions that the operating systems run on.

I ran fdisk -l and got the following:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7bca3e72


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    99274751    49533952   83  Linux
/dev/sda3        99274752   304074751   102400000    7  HPFS/NTFS/exFAT
/dev/sda4       304074752   488394751    92160000    7  HPFS/NTFS/exFAT


/dev/sda4 is the partition I need to recover.

Please help!!!

---

### Post by spencer the great on 2014-01-29
Does it mount correctly in Windows?
Is it an MBR or GPT table?
What's the error message when you try to mount it?

If it's a GPT table, and it's corrupted, try this [http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table)

---

### Post by EnriqueFabuloso on 2014-01-29
It doesn't mount in Windows or Ubuntu.
How do I check MBR or GPT?
I can still boot into Windows and Ubuntu.

Error mounting /dev/sda4 at /media/usernan/Storage: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/usernan/Storage"' exited with non-zero exit status 18: Failed to open ntfs attribute: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sda4': No such file or directory


I installed gdisk and got this:

Type device filename, or press <Enter> to exit: /dev/sda4
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Exact type match not found for type code 4F00; assigning type code for
'Linux filesystem'
Exact type match not found for type code 7300; assigning type code for
'Linux filesystem'
Exact type match not found for type code 2B00; assigning type code for
'Linux filesystem'
Exact type match not found for type code 6100; assigning type code for
'Linux filesystem'


Warning! Secondary partition table overlaps the last partition by
3587965843 blocks!
You will need to delete this partition or resize it in another utility.


Command (? for help):

---

### Post by oldfred on 2014-01-30
Do not convert to gpt. 

You have MBR(msdos) as fdisk does not work on gpt partitioned drives.
Windows will only boot from MBR drives with BIOS and only from gpt drives with UEFI.

Have you run chkdsk from Windows on your shared data partitions?

---

