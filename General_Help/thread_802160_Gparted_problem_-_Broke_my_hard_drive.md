---
title: "Gparted problem - Broke my hard drive?"
date: 2008-05-21
forum: General Help
---

### Post by saj0577 on 2008-05-21
Hey,

I have an external Hard Drive what happened is I had a bootable area on it and by accident and I deleted the first partition(bootable one) so it started messing about and not working at all. I could access some of the files on the other partitions but not them all otherwise i would get an I/O error i think it was. 

So I deleted all partitions. I can still create partitions on it but I cant format the partitions on it.

Also my hard drive has now only got a capacity of 465gb where as before my problems it appeared as around 498GB.

Any help would be great.

The gparted report is attached.

Saj

---

### Post by wpshooter on 2008-05-21
If you don't have ANYTHING on the drive that you need to keep, then get [www.killdisk.com](www.killdisk.com) and WIPE the drive completely clean and then attempt to use it.

Good luck.

---

### Post by saj0577 on 2008-05-21
Okay trying that now hope its a ubuntu program :)

Saj

---

### Post by saj0577 on 2008-05-21
it will only do it to external HD yeah?

---

### Post by wpshooter on 2008-05-21
It is NOT a Ubuntu program, it is bootable from either a CD or floppy disk.  It will WIPE what ever drive you wind up pointing/instructing it to.

P. S. - Do not point it to a drive that you have anything on it (like if you have Ubuntu installed on another drive) or it will WIPE it.  Just make sure that you know what you are doing before you hit that enter key after typing in "ERASE-ALL-DATA".

---

### Post by saj0577 on 2008-05-21
Okay.
I will give it ago and hope it helps. Will report back in about 10 minutes.

Saj

---

### Post by saj0577 on 2008-05-21
External HD doe snot appear on the list of hard drives to erase.

There are no partitions on the extneral HD at the minute.

But I can create unformatted partitions.

Saj

---

### Post by wpshooter on 2008-05-21
Then in that case you are probably going to have to erase it with some software that will run within an O/S.  It think there is one in Ubuntu under Synaptic called gparted or something like that.  I have never used it except as part of the Ubuntu O/S installation process.

---

### Post by saj0577 on 2008-05-21
If you look at the thread mate that is what progrma i get the error with mate.

Saj

Is it possible for me deleting a bootable partition for it to kill the HD forever?

---

### Post by sixdrift on 2008-05-21
Just a thought, and this arguably is little different than using gparted, but have you used the fdisk command directly from Ubuntu? You would need to know your drive specifics, but it allows more direct control of the partitioning.

Be careful though, fdisk is the disk partitioner. Make sure you know your device names and point it appropriately or you will wipe out something important.

---

### Post by saj0577 on 2008-05-21
So what commands would i use to totaly wipe

sdc

in order to put it back to factory standards as such..

---

### Post by irw on 2008-05-21
have you tried fdisk, and formating the drive / partitions from the command line?

Make sure you know exactly which partitions you are dealing with - you don't want to wipe the HD in your machine.:shock:

---

### Post by irw on 2008-05-21
snap!  great minds think alike!

in a terminal, I would start with ```
fdisk -l
```which will list your partitions; make sure you know which is which.

Then```
sudo fdisk /dev/sdX  (put correct disk here)
```.
When fdisk is running, type P to get a list of partitions, M to get a list of commands.  It is fairly self explanatory.  Finally W to write the changes to disk.  If you get confused / change your mind, Q will quit the program without committing any changes to the disk.

---

### Post by saj0577 on 2008-05-21
```
stephen@Stephen-Laptop:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
stephen@Stephen-Laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8b7d8b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2675     1951897+  82  Linux swap / Solaris
/dev/sda3            2676        7296    37118182+   5  Extended
/dev/sda5            2676        2802     1020096   83  Linux
/dev/sda6            2803        4077    10241406   83  Linux
stephen@Stephen-Laptop:~$ sudo fdisk /dev/sdc

Unable to open /dev/sdc

```

---

### Post by wpshooter on 2008-05-21
> **saj0577 said:**
> If you look at the thread mate that is what progrma i get the error with mate.

Saj

Is it possible for me deleting a bootable partition for it to kill the HD forever?

Yes, sorry, I just remembered that.

No, I doubt that any permanent damage is done.

Like the next poster said, try using fdisk.

---

### Post by irw on 2008-05-21
I have found it is always worth pasting errors into google; this gives you [this.]("http://www.google.co.uk/search?hl=en&q=ext2fs_mkdir%3A+Attempt+to+read+block+from+filesystem+resulted+in+short+read+while+creating+root+dir+&btnG=Google+Search&meta=&aq=f")

In particular look at [this]("http://segva.blogspot.com/2007/05/how-not-to-partition-external-hdd-on.html") - it sounds like the same problem as you have.

---

### Post by saj0577 on 2008-05-22
```
sudo parted /dev/sdc
Error: Could not stat device /dev/sdc - No such file or directory.        
Retry/Cancel?      
```

---

### Post by saj0577 on 2008-05-22
```
fsck /dev/sdc
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;


```


```

badblocks /dev/sdc
badblocks: No such file or directory while trying to determine device size

```

---

### Post by saj0577 on 2008-05-22
PARTED
```
(parted) mkfs 1 ext2                                                      
Error: Input/output error during write on /dev/sdb  
```

GPARTED
SAME AS BEFORE

Saj

---

### Post by saj0577 on 2008-05-22
Created a 1GB fat32 partition and I have been growing it by 10gb everytime no problms so far and I am at 80gb so i think it is a problem with the way my computer formats ext maybe?

Saj

---

### Post by irw on 2008-05-22
Ironically, after responding to this, I have today had a problem with bad superblocks on an sdcard I was trying to copy a disk image to.
I tried everything I could - fdisk, fsck, e2fsck, mk2fs, parted, gparted - with no success. ](*,)

This evening solved the problem in 5 minutes using cfdisk (on my eeePC) - now the card is working normally! :)

---

### Post by saj0577 on 2008-05-25
How i install it?

Saj

---

### Post by fjgaude on 2008-05-25
It's in the repositories of Ubuntu... just use apt- get or Synaptic for cfdisk. It's very nice.

---

### Post by mobileking on 2008-05-25
can you explain :confused:

---

### Post by fjgaude on 2008-05-26
```
sudo apt-get install cfdisk
```

Then learn about the program:

```
man cfdisk
```

---

### Post by saj0577 on 2008-05-26
Cant find the package.


Saj

---

### Post by saj0577 on 2008-05-26
NO cfdisk package found at all even afte
sudo apt-get update
sudo apt-get upgrade
sudo apt-get update

Saj

---

### Post by saj0577 on 2008-05-26
Any windows apps to this so I can try them too on my other computer. I just want it to work again.

Saj

---

### Post by irw on 2008-05-26
cfdisk is in the util-linux package (I think) which is in the repositories:```
sudo apt-get install util-linux
```

---

### Post by saj0577 on 2008-05-26
Thanks.

Saj

Il see if that works to fix my HD

---

### Post by saj0577 on 2008-05-27
cfdisk gives a fatal error and now the hard drive wont even connect. Gparted just keeps going in circles when i refresh it.

Saj

Any help please i need to fix this HD i dont care if its a windows app just something that will fix it please.

---

### Post by irw on 2008-05-28
Is this the error you get?
```
[CENTER]FATAL ERROR: Cannot open disk drive
Press any key to exit cfdisk[/CENTER]
```

I get this when trying to use cfdisk without root privileges / sudo.

I also get an error when dealing with encrypted disks.

---

### Post by saj0577 on 2008-05-28
I get the error once writin to the disk and it then becomes disconnected, i been reseaching and i came acros that my hard drive "Western Digital" always have problems, it worked before so its quite weird how it stopped working now.



Saj

---

### Post by saj0577 on 2008-05-28
Got it to work. But now i get read-only error everytime i try to put anything on it.

Any help/guidance anyone?

Saj

---

