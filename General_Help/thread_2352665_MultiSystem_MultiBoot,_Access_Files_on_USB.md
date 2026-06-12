---
title: "MultiSystem MultiBoot, Access Files on USB"
date: 2017-02-14
forum: General Help
---

### Post by webmanoffesto on 2017-02-14
I created a MultiSystem MultiBoot Flash Drive (disk on key)
But I have files on there that I want to access after I boot up an OS.
I don't see how to access a file in MyFiles which is in the root directory after I boot up an OS.
It shows me Desktop, Documents, Downloads, all of which are empty of course.

I found information here, but it's a little beyond me
[https://linuxexpresso.wordpress.com/2010/03/14/mount-partitions-in-terminal-fstab/](https://linuxexpresso.wordpress.com/2010/03/14/mount-partitions-in-terminal-fstab/)

MultiSystem [https://sourceforge.net/projects/multisystem/](https://sourceforge.net/projects/multisystem/)

---

### Post by ajgreeny on 2017-02-14
How large is the MultiSystem MultiBoot Flash Drive?

If there is sufficient empty space on the flash drive it may be possible to create a second partition on it that can be used for such purposes, but we need more info first.

You will need to use gparted from either another live USB or even an installed OS to create the new partition, assuming it can be done at all.

---

### Post by C.S.Cameron on 2017-02-14
Create an ext partition for the files you want to access.

---

### Post by webmanoffesto on 2017-02-15
Thanks. Using GParted I copied all the folders and files to a backup

Then on my Flash Drive I created 
... /dev/sdb1, FAT32, 500 MB, and
,,, /dev/sdb2, FAT32, 31.5 GB

I understand that FAT32 will be helpful if I want to use it on a Windows machine,
and I think that in some cases a Windows machine will only read the first partition (500MB for small files I may need)

Then I copied all the files and folders back to sdb2
 
I plugged this in to a Linux machine, and restarted it so I could boot up MultiSystem, but it didn't open. It boots the regular OS Linux, not the MultiSystem which is on the USB Flash Drive

When I boot up my usual (on-Hard-Drive) OS, when I open the MultiSystem program it only sees the first 500 MB partition. But if I go to "Files" file browser I can go to both partitions. This doesn't make sense. Can you help me resolve this problem.

---

### Post by ajgreeny on 2017-02-15
If you need to save files which you can then read with Windows and vice-versa, it will probably be easiest to simply use a second separate USB flash drive.

I do not use Windows any more and I had forgotten that it can only see and use the first partition on a USB drive; I am a bit surprised that has not changed in the 11 years I've been free of Windows, but it sounds as if it is still the same.

For your current boot problem I suspect that in copying your backup files back to your multisession USB you have simply broken the boot system used by it, but I do not know enough to be able to tell you how to put it right.  As it is supplied as an ISO file, I assume you have to install it as you would an operating system or a live OS, and you can not simply copy those to and from a USB, but have to "burn" them as an image.

---

### Post by yancek on 2017-02-15
Windows will recognize any partition with a windows filesystem on it on an actual external hard drive but not what are referred to as flash/pendrives.  Obviously, they could do this on a flash/pendrive they just don't want to.

 How did you create your multiboot/multisystem flash drive?  Did you do it manually or use some software designed for that purpose.  If the latter, what software did you use?

The steps described above in post 4, was that done in your attempts to create a partition which you could access when booting the multisystem flash?  That won't work the way it is described because you have move the location of the boot files.  What systems do you have on the multisystem flash?  Are they all Linux?  Are any of them persistent?  If they are Linux and not persistent, you could shrink the partition and create an additional partition on which to store data on the flash drive but you would have to create a mount point each time you boot and then mount the partition.

More information on exactly how you did what you did and what you have is needed.

---

### Post by C.S.Cameron on 2017-02-16
Multisystem Multiboot creates a single FAT32 partition.
Anything on this partition is already accessible to Linux, Windows and OSX.
Just make a folder for data in this partition.
You do not need a second partition unless you want to make one of the OS's persistent.
(in which case create an ext partition and label it casper-rw).

In order to access this data folder while booted from the multiUSB go to computer/isodevice.
The folder is read only unless accessed by root, use sudo nautilus or better yet install gksu and open the folder read/write using gksu nautilus.

---

