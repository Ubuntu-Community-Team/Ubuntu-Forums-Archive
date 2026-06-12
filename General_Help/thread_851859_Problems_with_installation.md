---
title: "Problems with installation"
date: 2008-07-07
forum: General Help
---

### Post by vidur on 2008-07-07
Hi guys...I'm a beginner on linux and tried installing Ubuntu 8.04.
Now I had a brand new hard disk with only Windows Vista OS files on it.

While partitioning my disk..the C: drive got formatted and consequently Vista was gone.
As i had no files on that, I'm not worried about loss of data.

Now with Ubuntu installed..I try to install Vista but it says " The drive needs to be a fat2" or something as it is having ext3 and swap which I made for linux.

whats the way out?

---

### Post by iaculallad on 2008-07-07
> **vidur said:**
> Hi guys...I'm a beginner on linux and tried installing Ubuntu 8.04.
Now I had a brand new hard disk with only Windows Vista OS files on it.

While partitioning my disk..the C: drive got formatted and consequently Vista was gone.
As i had no files on that, I'm not worried about loss of data.

Now with Ubuntu installed..I try to install Vista but it says " The drive needs to be a fat2" or something as it is having ext3 and swap which I made for linux.

whats the way out?

Did you create any NTFS/FAT32 partition on your drive when you installed Hardy? How did you partition you're Drive using Gparted, manually or Gparted's automatic settings?

---

### Post by vidur on 2008-07-07
I used manual partition.

12 GB for ext3 mount point '/'

1 GB for swap

---

### Post by iaculallad on 2008-07-07
> **vidur said:**
> I used manual partition.

12 GB for ext3 mount point '/'

1 GB for swap

Without a /home partition? If your system is a fresh install, I would suggest that you do a re-installation  of Ubuntu (that's if you had not save any data yet + no configurations done yet), only this time, create a FAT32/NTFS partition for your vista OS.

What's the size of your hard drive?

---

### Post by vidur on 2008-07-07
250 GB hard drive -- 160 GB C:\ drive
90 GB D:\ drive


can you pls tell what will be the best method to partition..should i use gparted this time?

and the exact partitions which i use? thanks

---

### Post by iaculallad on 2008-07-07
> **vidur said:**
> 250 GB hard drive -- 160 GB C:\ drive
90 GB D:\ drive


can you pls tell what will be the best method to partition..should i use gparted this time?

and the exact partitions which i use? thanks

With that huge amount of disk space, you could do:

/ partition = 20GB
/home partition = 40GB (You could still increase it if you want to)
swap partition = say, 1024MB? That depends on the size of your RAM still.

Create a 30GB NTFS partition for your vista OS.

Remaining disk space would be up to you - For Backup partition maybe.

Do the manual Gpartitioning method.

EDIT: The values I posted above are variables. You could still change it to the partitioning scheme w/c could fit your need.

---

### Post by vidur on 2008-07-07
Now, I have reinstalled ubuntu with a 100 GB NTfS partition for windows....yet on installing vista when i click on use that particular partition it says " Windows cannot find a system volume meeting its criteria for installation".

:(

---

