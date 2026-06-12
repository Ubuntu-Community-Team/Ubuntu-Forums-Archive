---
title: "Hard Drive saying no space! I HAVE SPACE!"
date: 2008-04-26
forum: General Help
---

### Post by Joseph_Schafer on 2008-04-26
I have ubuntu 8.04, and have had a partition with a ubuntu 6.something AMD64. I never used it, so i replaced it with the most recent version of Freespire. 

I did not like freespire, and am just going to let it sit there on my disk for a while. But after I installed it (or more correctly, after I moved too many files over from old partition and filled this one.) i ran out of disk space. I deleted my trash (had about 10 gigs in it!) but whenever I am logged in my computer says that I have no disk space. If I go into terminal and log in as another user (not graphically) it says I have 10 gigs left. Gparted also says that. Another problem (though it may be unrelated) is that when I press the log out button all the panels crash.

With this bug I cannot even press the back button on my browser, for it wont store my previous web pages as files. I cannot play any games, for it wont recognse. I cant even create an empty text document. Please help.

Also when I boot up, Grub doesnt go "hi ubuntu!" but instead each time i have to manually boot up by editing freespires replacing 
(hd0,0) with (hd0,2), something=/dev/sda1 with something=/dev/sda3

So i want 2 answers really.
1. Why cant I write stuff (how do i fix it!)
2. How do i put Ubuntu in Grub? it was there before with 2nd partition of ubuntu64!

---

### Post by tamoneya on 2008-04-26
it may be a different partition that is full.  Post the output of ```
sudo fdisk -l
```To edit GRUB you should look near the bottom of /boot/grub/menu.lst.  You can do this with ```
sudo nano /boot/grub/menu.lst
```

---

### Post by Joseph_Schafer on 2008-04-26
kit@The-Chrisinator:~$ sudo fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000384bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13137   105522921   83  Linux
/dev/sda2           29766       30515     6024375    5  Extended
/dev/sda3           13138       29765   133564410   83  Linux
/dev/sda5           30144       30515     2988058+  82  Linux swap / Solaris
/dev/sda6           29766       30143     3036222   82  Linux swap / Solaris

Partition table entries are not in disk order
kit@The-Chrisinator:~$ 

and i edited the other thing and added a 

configfile(hd0,2)/boot/grub/menu-normal.lst

below the one that was exacly like that, except hd0,0

---

### Post by imtheguru on 2008-04-26
> **Joseph_Schafer said:**
> I moved too many files over from old partition and filled this one.) i ran out of disk space.
...
I deleted my trash (had about 10 gigs in it!) but whenever I am logged in my computer says that I have no disk space. If I go into terminal and log in as another user (not graphically) it says I have 10 gigs left. Gparted also says that. The disk may not be completely full, but the user space is. The problems with files in /home are symptomatic of the user partition being full.

Ext2fs reserves 5% of the partition space for root. This is to allow the partition to be accessible and workable even if users fill up their quotas. By extension, ext3fs has the same behaviour.

Sources [[http://martin.hinner.info/fs/Filesystems-HOWTO/Filesystems-HOWTO-6.html]](http://martin.hinner.info/fs/Filesystems-HOWTO/Filesystems-HOWTO-6.html])
[[http://linux.die.net/man/8/tune2fs]](http://linux.die.net/man/8/tune2fs])

---

