---
title: "Can not mount 3TB External HDD"
date: 2014-08-11
forum: General Help
---

### Post by amjjawad on 2014-08-11
Hi,



[ATTACH=CONFIG]255395[/ATTACH]

[ATTACH=CONFIG]255396[/ATTACH]

```
Failed to read last sector (732566015): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfsprogs / ntfs-3g.
```


I have tried:

```
lubuntu@lubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... Failed to read last sector (732566015): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
FAILED
Attempting to correct errors... Failed to read last sector (732566015): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
FAILED
Failed to startup volume: Invalid argument
Failed to read last sector (732566015): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
lubuntu@lubuntu:~$ 


```

I have tried:

```
lubuntu@lubuntu:~$ sudo mount -r /dev/sda1 /mnt
Failed to read last sector (732566015): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
lubuntu@lubuntu:~$ 


```

I have tried:

```
lubuntu@lubuntu:~$ sudo mount -o  ro,noload /dev/sda1 /mnt
Failed to read last sector (732566015): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
lubuntu@lubuntu:~$ 

```

I have tried
testdisk

I managed to copy 'some' files over night. After 24 hours, the computer was stuck and had to reboot and start all over again: attempt 1 with Xubuntu 14.04 LiveUSB

I then had to start all over again with another 24 hours and then I woke up and found the machine was stuck, yet again and that was attempt 2 with Lubuntu 14.04 LiveUSB

I managed to copy 'some' files with both tries but I do NOT know if that is all because the two processes were stopped and I can NOT waste another 24 hours to re-do the whole thing yet again for the 3rd time.

My Q is as per what I posted above with error messages, etc ..

How to solve this issue so that I can mount the drive easily and normally without all this headache?

Thank you!

---

### Post by oldfred on 2014-08-11
Did you originally partition with Windows. Or is this a proprietary vendor configuration intended to work with XP as XP does not work with gpt partitioning?

It looks like you have MBR partitioning with has a 2TiB or 2.2TB max and will not work with a 3TB drive. But some external drives with Windows use a special MBR of 2TB and another drive mounted somehow. But that is not standard.

       MBR tech details including 2TiB limit and GPT link
[URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record

      [/URL]
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

    
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

What does this show?

 sudo apt-get install gdisk
sudo gdisk -l /dev/sda
GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

 
    [URL="http://en.wikipedia.org/wiki/Master_boot_record"]
[/URL]

---

### Post by amjjawad on 2014-08-11
Hello oldfred and thanks a lot for your reply :)

> **oldfred said:**
> Did you originally partition with Windows. Or is this a proprietary vendor configuration intended to work with XP as XP does not work with gpt partitioning?

The drive is not mine. It is for a friend I am trying to help. It is an external drive. I had to break the exernal plastic case and it is no more can be used unless I plug it to a PC which I have here for such pruposes (backup and stuff).

My friend just want to save the files as he cares about and he approached me because his technical skills are very limited and he can't do it by himself.


> What does this show?

 sudo apt-get install gdisk
sudo gdisk -l /dev/sda


```
lubuntu@lubuntu:~$  sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 82560E3E-A4D9-4AAC-B679-9784B3972E78
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1565565806 sectors (746.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      4294969342   2.0 TiB     0700  Microsoft basic data
lubuntu@lubuntu:~$ 


```
[URL="http://en.wikipedia.org/wiki/Master_boot_record"]
[/URL]

---

### Post by oldfred on 2014-08-11
I would not write the gpt unless you have a good image backup.

I have seen several others with these large drives and strange partitions or configurations. Not sure if they were able to resolve issues or not. A few were just data written like a floppy drive without partitions and they did not recover data, some have unusual sector sizes or use something that Linux sees as RAID or LVM.

Another older thread.
[http://ubuntuforums.org/showthread.php?t=2198460](http://ubuntuforums.org/showthread.php?t=2198460)

---

