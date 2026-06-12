---
title: "I need help accessing an NTFS partition through Ubuntu"
date: 2007-03-11
forum: General Help
---

### Post by moot on 2007-03-11
When I installed Ubuntu earlier today, I originally intended to install it on my external HDD, which was mostly blank save for less than a gig of files put there by Windows which were hidden.  However, when I went through the Ubuntu installation process and got to the point where I had to select which partitions I wanted to use for / and swap I accidentally selected my internal hard drive, which has Windows XP SP2 on it along with all of my other files.  I still can't believe I made such a dumbass mistake, and I ended up splitting my internal hard drive into 3 partitions, the first of which had Windows on it, the second of which had / and the third of which was my swap partition.  After resizing and formatting the latter 2 partitions as ext3 and linux-swap respectively, I installed Ubuntu and when I saw that Windows XP showed up in Grub I thought that everything was cool.  That is, until I actually attempted to boot XP.  I saw the splash screen followed immediately bysomething along the lines of "Error: cannot find autochk, skipping AUTOCHECK" and then my computer went back to POST.  I booted into Ubuntu, thinking that I could access whatever files I had on the first partition from there, installed NTFS-Configuration Tool, mounted the drive to /media/lol and then attempted to browse the contents of that part, only to find that it didn't list any contents, but Disk Manager said that there were 74.53 GB of files on the first partition and 25.93 GB of free space.  If it helps, here's a screenshot of what Disks Manager says:

[IMG]http://i48.photobucket.com/albums/f203/goldencream/Random/lol.jpg[/IMG]

I've already downloaded UBCD ([http://www.ubcd4win.com/]("http://www.ubcd4win.com/")) and Active Partition Recovery ([http://www.partition-recovery.com/]("http://www.partition-recovery.com/")) in case that's helpful.  Note that I do not have my original Windows XP CD, but I can get a hold of another one.  However, I would like to do either of the following without having to get a hold of another copy of XP:


1. Fix this autocheck problem and boot into Windows XP, then immediately back up everything.

2. Make NTFS-Configuration Tool read and write the files on my first partition and immediately back them up.

---

### Post by aidanr on 2007-03-11
> Posted by: fibbi

The autochk bug in winXP comes from trying to boot XP from a primary partition that is not currently active (IE, its "hidden NTFS"). This would usually come from having another OS installed, but also possibly from simply doing a bad job with your partitioning scheme. Either get your hands on a copy of the Partition Magic Boot Disks, or if you are comfortable with fdisk, use that. Set your XP partition to active, and you'll be set.

try setting the partiton active with [gparted]("http://gparted.sourceforge.net/livecd.php") (right click on partition -> manage flags)

---

### Post by moot on 2007-03-11
> **aidanr said:**
> try setting the partiton active with [gparted]("http://gparted.sourceforge.net/livecd.php") (right click on partition -> manage flags)

I made a gparted LiveCD, copied everything from the first partition to my external hard drive and checked the flags, non of them said anything about being active, my first partition just had the "boot" flag checked and my second and third partitions had nothing checked.


Edit:  Now Disc Manager is telling me I don't have the permissions to view my extrenal hard drive and I realized that I may have mounted my first partition incorrectly with NTFS-Config because gparted told me it was unmounted.

---

### Post by taurus on 2007-03-11
Try something like these from a terminal, Applications -> Accessories -> Terminal.

```
sudo umount /dev/sda1
sudo mount -t ntfs /dev/sda1 /media/lol -o nls=utf8,umask=0222
df -l
```

---

### Post by moot on 2007-03-11
> **taurus said:**
> Try something like these from a terminal, Applications -> Accessories -> Terminal.

```
sudo umount /dev/sda1
sudo mount -t ntfs /dev/sda1 /media/lol -o nls=utf8,umask=0222
df -l
```

Edit: I can see the files on my first partition and even open some of them, but I can't write to the first partition or boot into Windows, I got the same autochk error.

Edit2: It also becomes un-mounted after I reboot,

---

### Post by dexter on 2007-03-11
> **moot said:**
> Edit: I can see the files on my first partition and even open some of them, but I can't write to the first partition or boot into Windows, I got the same autochk error.

Edit2: It also becomes un-mounted after I reboot,

Ubuntu is not able to write to ntfs drives by default. You'll have to install the ntfs-3g driver, check out this topic about it : [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

Since you're mounting the drive manually, you'll have to do it every time by hand. You can automount the disk by adding it to /etc/fstab . This is also explained in the tutorial above.

---

