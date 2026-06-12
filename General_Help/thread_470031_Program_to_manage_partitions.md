---
title: "Program to manage partitions"
date: 2007-06-10
forum: General Help
---

### Post by tL0z on 2007-06-10
Hello,

I would like to remove some space to the Windows partition in order to increase the Ubuntu's partition space. I tried to run Norton Partition Magic on Windows but it gave me an error (driver letter not recognized - possibly because I installed Ubuntu). Therefore, I need a smilar program for Ubuntu.

Is there any good partition manager for Ubuntu?

Thanks

---

### Post by logos34 on 2007-06-10
**sudo apt-get install gparted**

There's also **[Gparted live CD ]("http://gparted.sourceforge.net/livecd.php")**

---

### Post by nqsonk9 on 2007-06-10
If you're using Gnome as your defaut desktop, gparted is the most common application for partitioning, i think.
Just go to terminal and code *sudo gparted*, if gparted 's not available on your machine, install it by *sudo apt-get install gparted*

---

### Post by Jonne on 2007-06-10
Use the liveCD, gparted is included (it's what you used when you installed Ubuntu anyway).

---

### Post by logos34 on 2007-06-10
The version of gparted on the Ubuntu live cd is not as good as the Gparted live cd (which also has couple of useful utilities not on the former).  It's easiest to try it from the desktop first.

---

### Post by tL0z on 2007-06-11
Is the program stable? I don't want to lose my files. :neutral:

I may use the one which has to be installed on Ubuntu.

---

### Post by indytim on 2007-06-11
Like all other partition editors, it's only safe to the point where you know what you're doing.  Before doing any partition work, backup-backup-backup.  I would recommend (especially while working with a NTFS partition) that you do one complete task at a time.  In other words, if you want to resize your NTFS partition and re-allocate the new space to the adjoining partition, then downsize your NTFS partition and complate that task.  After that has been completed then resize your ext3 to the new space created by reducing your NTFS.

Hopefully this will keep your system happy.

Good Luck,

IndyTim

---

### Post by Wim Sturkenboom on 2007-06-11
Your files are not important to you, else you should have made backups long ago.

---

### Post by tL0z on 2007-06-11
I have backups of my personal files (such as thunderbird files). But I don't have backups of my music and videos for instance.

I think I'm going to use the Live CD instead. It seems that I can't resize partitions when running the program on Ubuntu.

---

### Post by Jonne on 2007-06-11
You won't be able to resize a partition to grow towards the beginning of the disk, so assuming your ntfs partition is the first one, you'll have to shrink it, then create a new partition between your ntfs partition and your ext3 ubuntu partition, copy your files over to the new partition, delete the last partition and grow your new partition. (unless the gparted live CD can do that, i know i had this problem with gparted on the ubuntu cd).

Or alternatively you could choose to have your home directory on a seperate partition (which is recommended) and then use the partition between your ntfs and old ubuntu partition for the OS (Ubuntu itself only needs about 10gigs, my root partition is about 600MB big). You'll need to reinstall ubuntu for this, but that's pretty painless, just remember which packages you were using, and save any conf files you edited to your home directory as backups (and back up your home directory on an external hd or a dvd or something).

It all depends on how big your disk is, how big you want your partitions to be, and how much free space you have left.

---

### Post by timcredible on 2007-06-11
> **tL0z said:**
> 
I think I'm going to use the Live CD instead. It seems that I can't resize partitions when running the program on Ubuntu.

you can't resize a mounted partition, so you'll have to run a live cd (your ubuntu cd will work if you choose install and then choose manual for partitioning, do your changes, write the partition table, but don't do the install, but the gparted cd will probably be better).

---

### Post by tL0z on 2007-06-11
I'm having a problem. My Ubuntu partition and the NTFS partition I want to resize are in an "extend" partition, and I can't resize it! I'm going to have to reinstall ubuntu "out of" the extended partition.

---

