---
title: "[SOLVED] Unable to access second partion of 1st drive nor entire secon drive"
date: 2007-09-18
forum: General Help
---

### Post by MacDuff on 2007-09-18
After doing a hardware upgrade and installing a second hard drive, I installed Ubuntu 7.04 with no problem on a partition of my IDE hard drive.

I can see the second partition of drive 1  but I cannot create directories nor files in it.

I can see the second hard drive (Sata11) formatted NTFS but I cannot create directories in it.

Here is the result of fsec

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20023   160834716    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7931    63705726   83  Linux
/dev/hdb2   *        7932       23650   126262867+  83  Linux
/dev/hdb3           23651       24321     5389807+   5  Extended
/dev/hdb5           23651       24321     5389776   82  Linux swap / Solaris

The drives are owned by root and I cannot change the permissions of them.
By the way, there is nothing on either of them if that makes any difference. 
Can anyone tell me how to solve this problem?

Mac

---

### Post by rsambuca on 2007-09-18
You can not write to ntfs drives without loading the ntfs-3g drivers first.  Install both "ntfs-3g" and "ntfs-config" (they are in Synaptic Package Manager).  Then run ntfs-config and it well step you through setting up your ntfs drive as read and write.

---

### Post by MacDuff on 2007-09-18
Thanks.  I will give that a try. 

 Funny that it did not seem to be a problem on the first install but that may have been because the original install was a dual boot whereas this time I cleared the drive of Windows before installation.

Mac

---

### Post by rsambuca on 2007-09-18
> **MacDuff said:**
> Thanks.  I will give that a try. 

 Funny that it did not seem to be a problem on the first install but that may have been because the original install was a dual boot whereas this time I cleared the drive of Windows before installation.

Mac

Huh?  If you erased Windows, why do you have an ntfs drive?  The filesystem is not as good as ext3.

---

### Post by MacDuff on 2007-09-19
The box that I am devoting to Ubuntu will be my communications computer, will run 24 hours a day, and also serve as a type of network server on which I will back up files from my other computers.  The other machines are a collection of Windows XP and a dual boot (Ubuntu and XP).

I made the assumption that Windows can not write to ext3 format so it would be better to format those partitions, that may be used as file backups,  as NTSF.  As I become more knowledgeable about Ubuntu, it is my intention to install it on all the computers and they will then all be formatted to ext3 but until then, I thought there would be less risk of a problem by leaving the backup space as NTSF.

Am I wrong about that?  Any advice you can provide would be appreciated.

Mac

---

### Post by rsambuca on 2007-09-19
> **MacDuff said:**
> The box that I am devoting to Ubuntu will be my communications computer, will run 24 hours a day, and also serve as a type of network server on which I will back up files from my other computers.  The other machines are a collection of Windows XP and a dual boot (Ubuntu and XP).

I made the assumption that Windows can not write to ext3 format so it would be better to format those partitions, that may be used as file backups,  as NTSF.  As I become more knowledgeable about Ubuntu, it is my intention to install it on all the computers and they will then all be formatted to ext3 but until then, I thought there would be less risk of a problem by leaving the backup space as NTSF.

Am I wrong about that?  Any advice you can provide would be appreciated.

Mac

If it is just for backups, I am sure it will be fine either way.  Just for your future reference though, there is a [driver for XP]("http://www.fs-driver.org/") so that it can read/write to ext2/3 filesystems.  I use it and the ntfs-3g for linux, and have had no problems either way.  The nice thing with ext3 is that you never have to bother defragging the drive like you do with ntfs.

---

### Post by MacDuff on 2007-09-19
THANK YOU rsmabuca!

That is excellent information.  Now that I FINALLY have a properly functioning Ubuntu system (after 3 months of struggle that you don't want to hear about), I am finally making good headway courtesy of the good people on the forums (and a book or three).

Though it has been a challenge, I am sold on Ubuntu and each day I delight in discovering new features in the Linux OS and learning new skills.

Thank you so much for your help

Mac

---

