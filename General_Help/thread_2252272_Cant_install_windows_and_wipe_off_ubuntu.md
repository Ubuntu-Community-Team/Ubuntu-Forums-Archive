---
title: "Cant install windows and wipe off ubuntu"
date: 2014-11-10
forum: General Help
---

### Post by bloodeyed77 on 2014-11-10
ok so i have my windows disk and i wish to go back to windows for compatablity reasons mostly but i still like ubuntu :) but anyway when i put the disk in and go it says windows cannot be installed to disk 0 partition 1. and also says its of unrecognized type :/ please help!

---

### Post by yancek on 2014-11-10
If you are having problems installing a windows operating system, the best place to get info is the microsoft site or a windows forum.  Link below is to the microsoft support site which refers specifically to xp but should work with whichever windows version you have.  This is a very old page but basically use a Linux Live CD rather than the floppy with fdisk.  You can do the same with GParted.  

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

---

### Post by pfeiffep on 2014-11-10
> **bloodeyed77 said:**
> ok so i have my windows disk and i wish to go back to window for compatablity reasons mostly but i still like ubuntu :) but anyway when i put the disk in and go it says windows cannot be installed to disk 0 partition 1. and also says its of unrecognized type :/ please help!More than likely your hard disk was formatted by the Ubuntu installation to ext3 / ext4  which Windows doesn't recognize. Hopefully one of our moderators (OldFred) will provide one his usual comprehensive answers. 

If you really like Ubuntu, but find that you're unable to perform all the tasks that you're accustomed to on Windows you might consider a dual boot system):P. 

In the mean time please post your system specifics and Windows version as well as Ubuntu version

---

### Post by QIII on 2014-11-10
Hello!

If your Windows installation media will not let you repartition the entire drive as NTFS (the last time I installed Win 7, I'm pretty sure there was an option to format the drive), boot to a live Ubuntu session on optical or USB drive.

Install gparted (I don't believe it is installed by default any more)

```
 sudo apt-get install gparted 
```

Open gparted

```
 gksudo gparted 
```

Select the drive with Ubuntu on it.  Be absolutely sure you choose the correct drive!

Select all partitions to delete.  You should see the entire drive as unallocated space. Leave it unallocated or create a single NTFS partition.

Click apply.  It may take a while.

That should give you a disk as if you had bought it formatted for Windows and your install media should work.

---

