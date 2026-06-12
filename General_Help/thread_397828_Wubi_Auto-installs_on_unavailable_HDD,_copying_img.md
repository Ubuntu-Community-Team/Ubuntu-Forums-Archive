---
title: "Wubi Auto-installs on unavailable HDD, copying img files to another folder"
date: 2007-03-31
forum: General Help
---

### Post by cro on 2007-03-31
I've been testing WUbi on various hardware setups, and the latest test, on a custom-build machine with 1 SATA drive and 1 IDE drive has had problems. The disk with the largest free space is a partition on the IDE drive, however at boot this disk cannot be found.

Copying the wubi folder to the SATA drive fails with a 'cannot copy file: make sure the disk' etc error.

To resolve this error, and copy the .img files to another drive/folder, do the following:

Load a Windows command prompt
Navigate to the Wubi folder
Navigate to the disks folde
Type the following commands:
cacls root.img /P Everyone:R
cacls home.img /P Everyone:R
cacls swap.img /P Everyone:R

You will now be able to copy those files to the new folder/HDD. You might want to restore the permissions on the copied files:

Navigate to the folder you copied the files to.
Type these commands:
cacls root.img /P Everyone:N
cacls home.img /P Everyone:N
cacls swap.img /P Everyone:N

---

### Post by ago on 2007-03-31
> **cro said:**
> The disk with the largest free space is a partition on the IDE drive, however at boot this disk cannot be found.
Do you know why? Is it a lupin issue or a grub issue?

---

### Post by Spegelius on 2007-04-01
I noticed the file permission thing also when trying to move the files. There is a line in the Wubi AllocFile function which call cacls to set the permissions to None for everyone. It seems this bit of code is from Hello1024, a developer whos been away for a while now. I recall that this sort of behaviour was in discussion at the beginning of this project (yes, i've read through the original thread ;) ).

The question is, do those imagefiles need to be permission limited? It's more secure, yes, but those images can still be deleted by simply deleting the folder where the files are. And if moving them is needed, it's bit complicated to start changing permissions (though it's true that one rarely needs to). Maybe permissions could be given for Admin and user who is installing Wubi? Anyway, now that i know what's was the problem with the images, i see no problem with current state.

---

### Post by ago on 2007-04-01
> **Spegelius said:**
> The question is, do those imagefiles need to be permission limited?
Hello1024 set the restriction based on one of my old requests, but I asked that because the img files were originally all in 1 folder mixed with all other files and accidental deletion was an issue. Now the img files are in a dedicated "disks" folder, and it is generally more unlikely for people to accidentally remove a folder as opposed to a single file. If we have to set privileges that would be "r/w to admin group only", but in the one-user=one-admin windows world that is mostly meaningless. So I guess we could also simply remove the restriction, ecology2007 is having a look. Suggestions welcome.

---

### Post by ecology2007 on 2007-04-01
Thanks to cro and spegelius for raising the issue and narrowing down the possible options.
Fix commited.

---

### Post by ago on 2007-04-01
I am also interested in this problem > however at boot this disk cannot be found.


cro, feel free to send me a pm with further info. In particular it is important to understand whether it is a grub issue or a lupin one.

---

### Post by ecology2007 on 2007-04-02
> **ago said:**
> I am also interested in this problem 


cro, feel free to send me a pm with further info. In particular it is important to understand whether it is a grub issue or a lupin one.

It s probably grub. It is responsible for error 17 message.

---

### Post by cro on 2007-04-02
Yes, sounds about right. It gets past grub and fails on finding the wubi folder using the --find command (apologies for vagueness, I was doing the work a couple of days ago and am currently running on too little sleep :) )

---

### Post by cro on 2007-04-02
An update: I moved the wubi folder to the second partition on my SATA drive, renamed the one of my IDE drive (so there was only one :\wubi folder), and it installed fine, even without setting the file permissions back. I'll do some digging around this evening when I get a chance, see which partitions I can see under ntfs-3g, or anything else that I can find.

---

### Post by ago on 2007-04-02
The point to investigate is whether the wubi folder is not "found" for any reasons on some of your disks/partitions. Move it to one partition at the time and see which one works and which does not. Just make sure you have a single wubi folder at all times.

---

### Post by cro on 2007-04-03
OK, this is what comes of writing threads from memory...

My disk layout is as follows:
DISK0 (IDE), partitions E:, F:
DISK1 (SATA), partitions C:, D:

DISK0 is connected to IDE channel 0 (or 1 - whichever is the first one)
DISK1 is connected to SATA channel 0 (or 1 - whichever is the first one)

Following tests, I found the following (with only one instance of the wubi folder anywhere on any drive):
Copying \wubi to e: results in find --setroot failing
Copying \wubi to f: results in find --setroot failing
Copying \wubi to d: results in a proper boot and install.

The wubi folder I am using is a complete Ubuntu Feisty 7.04 install, patched up to last night, with NVidia 755 proprietary drivers installed and working, with a working implemetation of Beryl, with a 6Gb primary image file.

At boot, the find --setroot finds the /wubi/linux folder on hd(0,1)

And for completeness, here's fdisk-l when booted into Ubuntu (which sees both disks...):
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12210    98076793+   7  HPFS/NTFS
/dev/sda2           12211       24321    97281607+   7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551       19929   139596817+   7  HPFS/NTFS
```
I didn't bother trying c:, I figure it'll work OK.

---

