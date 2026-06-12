---
title: "Running out of space frequently"
date: 2016-01-21
forum: General Help
---

### Post by nathan73 on 2016-01-21
Hey,

This has been a consistent problem of mine for a long time. Every once in a while my Ubuntu will say that I have run out of space on the disk. I will admit that I am sharing the disk between Ubuntu and Windows 7 using Wubi, However, I contest that there must be more space than what meets the eye. I have no videos, no music, no images, and few text documents on this computer, as well as staving off updating (which also uses up space). And yet, this is what is coming up when I run df -h in terminal:

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       19G   18G     0 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           376M  1.3M  375M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   88M  1.8G   5% /run/shm
/dev/sda3       447G  141G  306G  32% /host
cgroup          1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sr0        1.2G  1.2G     0 100% /media/WB3000
/dev/sda1       100M  120K  100M   1% /media/DELLUTILITY

```

I've tried an application called ubuntu sweeper, which helped delete some things and delay the inevitable, but ever since I used it the first time it refuses to work anymore. It just crashes my computer. 

There are many other things I've tried, including something about duplicating the disk, but suffice to say nothing has worked so far except to delete copious amounts of data, which only delays the inevitable.

This is really critical as there is so little space now, the document I am working in will not save!!!

---

### Post by oldos2er on 2016-01-21
Wubi is not supported and no longer recommended.

You don't say anything about whether your system is a desktop or laptop, how many hard disks it has or their capacity. It would be helpful to have some info about your system. Perhaps it's time for a new larger disk?

---

### Post by nathan73 on 2016-01-21
I am using a Dell laptop. As for the disks, the result of sudo lsblk -o gives:
```

NAME   FSTYPE MOUNTPOINT         LABEL
sda                              
&#9500;&#9472;sda1 vfat   /media/DELLUTILITY DELLUTILITY
&#9500;&#9472;sda2 ntfs                      Recovery
&#9492;&#9472;sda3 ntfs   /host              OS
sr0    udf    /media/WB3000      WB3000
loop0  ext4   / 

```

I'm sorry I don't give more information, but I really have no other idea how to assess what is going on. As I said before, there is very little on this computer so I do not see why I would have to get a larger disc. Even if I did, I don't know how to safely replace it.

Please let me know if there is any other information I can give you to help me solve this.

---

### Post by hakuna_matata on 2016-01-22
> **nathan73 said:**
> 
including something about duplicating the disk
Do you mean [Resize and Duplicate WubiDisk]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk") ?

Did you also notice the the second technique ? [Resize WubiDisk]("https://help.ubuntu.com/community/ResizeWubiDisk")

If necessary, your **root.disk** is on** /dev/sda3 **because of mount point **/host **> ```
/dev/sda3       447G  141G  306G  32% /host
```
 [URL="https://help.ubuntu.com/community/ResizeWubiDisk"]



[/URL]

---

### Post by oldos2er on 2016-01-22
My suggestion would be to backup any needed data, uninstall Wubi and run a real install of Ubuntu on its own partition, with 15 - 20GB for / and as much space as you can spare (100GB?) for a separate /home partition. Wubi was never intended to be a permanent way to run Ubuntu, but more of a demo that would be simple to remove.

---

