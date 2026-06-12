---
title: "Dual booting after fully installing ubuntu"
date: 2014-08-23
forum: General Help
---

### Post by Peter111313 on 2014-08-23
Hey,
So I installed ubuntu on my computer because the windows 7 boot disk wasn't working. I fully installed it to my hard drive thinking I could partition it whenever I install windows 7. Now I'm looking around and I can't seem to figure out how to do it. I don't want to wipe my hard drive to install windows 7. Oh and I have ubuntu 14.04. Please help.

---

### Post by yancek on 2014-08-23
To get some specific advice, we would need some specific information from you such as the number of drives you currently have as well as the partitions you have and their sizes.  You can get this information from a terminal with these two separate commands:

```
sudo fdisk -l
```
```
df -h
``` 

Post that information here.

---

### Post by Peter111313 on 2014-08-23
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00087579


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1947510783   973754368   83  Linux
/dev/sda2      1947512830  1953523711     3005441    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1947512832  1953523711     3005440   82  Linux swap / Solaris
peter@Karen:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       914G   39G  829G   5% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.4G  4.0K  1.4G   1% /dev
tmpfs           288M  1.3M  287M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G   21M  1.4G   2% /run/shm
none            100M   36K  100M   1% /run/user

---

### Post by yancek on 2014-08-23
You have one enormous partition (sda1 in your output) on which Ubuntu is installed.  sda2 is an Extended partition in which you have one small swap partition (sda5).
Problem one is that windows won't boot from a logical partition so you need to create a primary for it, or at least its boot files.  The way to do that is to use a Linux system, the easiest thing would be if you still have the Ubuntu installation DVD/flash drive to shrink sda1, the Ubuntu partition.  Do not try to do this from the Ubuntu installation.  When you boot your Ubuntu/Linux, open a terminal.  You can do this by clicking on the dash icon (the ubuntu logo in the extreme upper right of the desktop) and in the Search box type:  terminal.  It will show the terminal icon, click in it to open it then type:  sudo gparted.  This will open the GParted partition manager and you can use that to shrink the partition and create another partition on which to install windows.  The link below is to a tutorial which is extremely detailed on how to use GParted.  There is a Table of Contents and Section 6 is on resizing.

 [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

You should then be able to install windows to the newly created partition.  It's been a long time since I've installed windows so hopefully you will be able to tell which is which because windows uses a different naming system for partitions and also doesn't recognize Linux filesystems.

---

