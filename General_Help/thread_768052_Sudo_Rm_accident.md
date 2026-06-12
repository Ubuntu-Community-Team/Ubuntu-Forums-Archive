---
title: "Sudo Rm accident"
date: 2008-04-26
forum: General Help
---

### Post by king vash on 2008-04-26
I accidently ran Sudo rm (not Sudo rm -rf) on my slave drive which had a fair amount of important info on it, I'm looking to recover it, this is what i know so far

sudo fdisk -l return the drive plus a partition
```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4340433f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS
```
it has been mounted and inside is a folder named "System Volume Information" with two files "MountPointManagerRemoteDatabase" and tracking.log"

I attempted to recover it using WinInteral ERD but it didn't find any files on the disk

I have attempted to use foremost ```
sudo apt-get install foremost
sudo foremost -w -i /dev/sdb1 -o /recovery/foremost

``` but it didn't recover any files. Help please.

---

### Post by tamoneya on 2008-04-26
using fdisk will not give you much useful information since fdisk looks at the filesystems and partitions.  rm -rf / will remove files from the partition but will leave the filesystem itself in place.  I am not familiar with file recovery though on linux.  I would guess that you are fairly out of luck though.  rm -rf / is a fairly unreversible action.

---

### Post by Rocket2DMn on 2008-04-26
There are companies that will charge you extraordinary amounts of money to try and recover data from broken or deleted hard drives, but I'm not very sure on their effectiveness.  From what I understand, the rm command is designed to make it very difficult to recover deleted data (for security reasons, I suppose).
Unless there is something on that drive that is worth a lot of money to you, I think you are out of luck.
IF you choose to take this path, do not use the hard drive at all anymore, or you rism overwriting the blocks of data that you want to recover.  You should unplug the drive from your computer and leave it that way.

---

### Post by SPr on 2008-04-26
[SystemRescueCD](http://www.sysresccd.org/) has PhotoRec on it that can recover many types of files not just picture files. Burn it to CD, boot from it, type "photorec" without the quotes and follow the prompts. The NTFS partition can be mounted and the instructions to do that are included in the welcome screen when the CD gets to the command line.

---

### Post by benfrasersimpson on 2008-04-26
I used ERD disk commander to recover data from an ntfs partition before, and it runs from a bootable disk based on XP, so that might be your best bet. ERD system commander 2007 has the lastest version on it.

---

### Post by king vash on 2008-04-26
I tried with ERD commander but with no success, it only found the files I listed above, I think the problem is that I remounted the drive as ntfs after deleteting it.

I losted my 20 page resource paper for history class, my game files (not that important), movie collection and 100 some other gigs of data, I have back ups of my documents from a month ago but not of the movies, or game files.

---

