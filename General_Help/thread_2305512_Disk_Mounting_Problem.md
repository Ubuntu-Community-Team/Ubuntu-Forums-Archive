---
title: "Disk Mounting Problem"
date: 2015-12-06
forum: General Help
---

### Post by saay2 on 2015-12-06
Hello everyone, 

I am a new Ubuntu user and don't know much about Linux. I have Ubuntu 14.04 LTS and Windows 7 installed in my Laptop. The USB drive doesn't mount automatically and I get the following error. 

Error mounting system-managed device /dev/sdb1: Command-line `mount "/media/sdb1"' exited with non-zero exit status 12: NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Your help will be much appreciated, thanks.

---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

In Windows 7 Might format the drive to FAT32 ?? ..

Try this solution .



Or if you choose another option put this command in Terminal

> 
mount /dev/sdb1 /media/data -t ntfs


If it does not work try this command:

> ntfs-3g -t /dev/sdb1 /media/data


Finally if it does not work try this command :

> sudo ntfsfix /dev/sdb1

---

### Post by saay2 on 2015-12-07
Hi Ricardo, 

I think if I change the filesystem to FAT32 I will lose my data. However, I tried the other options but didn't work for me. 

saay@saay-ThinkPad-X230-Tablet:~$ sudo mount /dev/sdb1 /media/data -t ntfs
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
saay@saay-ThinkPad-X230-Tablet:~$ 

---------------------------------------------------
saay@saay-ThinkPad-X230-Tablet:~$ sudo ntfs-3g -t /dev/sdb1 /media/data
ntfs-3g: Unknown option '-t'.


ntfs-3g 2013.1.13AR.1 external FUSE 29 - Third Generation NTFS Driver
        Configuration type 7, XATTRS are on, POSIX ACLS are on


Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2012 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson


Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>


Options:  ro (read-only mount), windows_names, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).


Example: ntfs-3g /dev/sda1 /mnt/windows


News, support and information:  [http://tuxera.com](http://tuxera.com)

------------------------------------------

saay@saay-ThinkPad-X230-Tablet:~$ sudo ntfsfix /dev/sdb1
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
NTFS signature is missing.
Unrecoverable error
Volume is corrupt. You should run chkdsk.

--------------------------------------

And I used the following command to check disk though not sure if it's correct?

saay@saay-ThinkPad-X230-Tablet:~$ sudo fsck /dev/sdb1
fsck from util-linux 2.20.1
fsck: fsck.ntfs: not found
fsck: error 2 while executing fsck.ntfs for /dev/sdb1

---

### Post by Ricardo_Velasco on 2015-12-07
> Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
NTFS signature is missing.
Unrecoverable error
**Volume is corrupt. You should run chkdsk.**

Greeting:

Your problem is very interesting, and try to emulate and emule¡¡.

Ride my USB Flash in NTFS.

And you told me I send out those mistakes here my emulation:

> root@ricardo-desktop:/home/ricardo# sudo ntfs-3g /dev/sdd /media/data


NTFS signature is missing.
Failed to mount '/dev/sdd': Argumento inválido
The device '/dev/sdd' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@ricardo-desktop:/home/ricardo# sudo ntfs-3g /dev/sdd /media/data
NTFS signature is missing.
Failed to mount '/dev/sdd': Argumento inválido
The device '/dev/sdd' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@ricardo-desktop:/home/ricardo# sudo mount /dev/sdd /media/data -t ntfs


NTFS signature is missing.
Failed to mount '/dev/sdd': Argumento inválido
The device '/dev/sdd' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


[B]root@ricardo-desktop:/home/ricardo# sudo ntfsfix /dev/sdb1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.
root@ricardo-desktop:/home/ricardo# [/B]


The problem was solved with the last command me to send you  
The shaded line

But look again your command line where you sent me the command output> Mounting volume... NTFS signature is missing.

FAILED

Attempting to correct errors... NTFS signature is missing.

FAILED

Failed to startup volume: Invalid argument

NTFS signature is missing.

Trying the alternate boot sector

NTFS signature is missing.

Unrecoverable error

**Volume is corrupt. You should run chkdsk.**


Your volume is corrupted and need to run the Check tool Windows Disk (CHKDSK) ..

Your problem is too interesting , the solution would be:

Enter Windows and run a chkdsk on your drive ..

If you do not know please comment to show you.

And then try to run the same command that started at the end of the solution

sudo ntfsfix /dev/sdb1


I hope this solution works , I have no alternative

Try¡¡


PD: Run this comand

> df -h


Show me what you see, you send to me screenshot


> _**Please send me a screenshot of yours device in Disk Utility**_

---

