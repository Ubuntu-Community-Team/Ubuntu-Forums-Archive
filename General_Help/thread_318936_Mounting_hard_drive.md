---
title: "Mounting hard drive"
date: 2006-12-14
forum: General Help
---

### Post by Ptah on 2006-12-14
Hello I hope someone can help me with this.  I have read around the forum looking for answers but would like someone to point me in the right direction.  My question is I am trying to mount my second hard drive.  I have already sudo fdisk -l and here is the result:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18696   150175588+  83  Linux
/dev/sda2           18697       19452     6072570    5  Extended
/dev/sda5           18697       19452     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18701   150215751   83  Linux
/dev/sdc2           18702       19457     6072570    5  Extended
/dev/sdc5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdh: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       30401   244196001    c  W95 FAT32 (LBA)


I would like to mount /dev/sdb and use it for storage and would like have it on boot up.  Can anyone help!

To help I installed gparted to find out if I formated the drive correctly, here is the output:

Filesystem:  ext3
size: 149.01 gib
path: /dev/sdb1
status:  not mounted
First sector:  0
Last sector:  312499999
Total sectors:  312500000

Warning:  
dumpe2fs 1.39 (29-May-2006)
dumpe2fs:  No such file or directory while trying to open /dev/sdb1

---

### Post by drphilngood on 2006-12-14
Here´s a nice guide to walk you through it:

[how_to_install_second_hard_drive_ubuntu_linux]("http://www.smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux")

Hope this helps!

---

### Post by rlozano on 2006-12-14
you can go visit the site of aysiu at [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu). it will give you alot fo information about your concern.

---

### Post by devnulljp on 2006-12-14
Looks like you need to format it.

sudo fdisk /dev/sdb
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-xxxxx, default 1): 1
Last cylinder or +size or +sizeM or +sizeK (1-xxxxxx, default xxxxx): xxxxxx
Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

Then you need to make a filesystem
mkfs.ext3 -b xxxxxxxx /dev/hdb1

---

### Post by Ptah on 2006-12-14
Thanks for the replies.  Looking at gparted it says it is an ext3, must I reformat it again to ext3?

---

### Post by aysiu on 2006-12-14
> **Ptah said:**
> Thanks for the replies.  Looking at gparted it says it is an ext3, must I reformat it again to ext3?
No. If it's Ext3 it's Ext3.

---

### Post by Ptah on 2006-12-14
Ok I followed pyshocats instructions to the letter.  I check gparted again to see if the drive was mounted but it was not.  What did I do wrong?  Also I should have let everyone I am using Edgy.

---

### Post by aysiu on 2006-12-14
The whole thing with GParted is just to make sure it's Ext3 (and not ReiserFS or some other Linux filesystem) and to see what your partition's name is. After that, GParted is completely out of the picture.

Next, you need to create a mount point (folder where the partition will appear) for /dev/sdb1 and also an /etc/fstab entry for it: ```
sudo mkdir /media/extrastuff
``` There, now we have a mount point for it. Let's edit the /etc/fstab file: ```
sudo nano -B /etc/fstab
``` Add in a line for your partition: ```
/dev/sdb1 /media/extrastuff defaults 0 0
``` Then save (Control-X, Y, Enter) and finally mount the partition: ```
sudo mount -a
``` Now, /dev/sdb1 should be mounted to /media/extrastuff. To make sure you have proper access to it, change ownership on the partition: ```
sudo chown -R ptah:ptah /media/extrastuff
```

---

### Post by Ptah on 2006-12-15
After sudo mount -a it said,  mount:  special device /dev/sdb1 does not exist.  Does this have anything to do with the warning information (Post #1-bottom)

---

### Post by aysiu on 2006-12-15
> **Ptah said:**
> After sudo mount -a it said,  mount:  special device /dev/sdb1 does not exist.  Does this have anything to do with the warning information (Post #1-bottom)
Oh. I didn't read the first post carefully enough. Here's the problem: ```
Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

**Disk /dev/sdb doesn't contain a valid partition table**
``` I think you should focus on this first. One of the following threads might help:
[Entire hard disk wiped out! Please help](http://ubuntuforums.org/showthread.php?t=165583)
[Reformatting my External HD - Help!](http://ubuntuforums.org/showthread.php?t=174962)

---

### Post by kylevan on 2006-12-15
Yeah, I was gonna suggest that you delete all the partitions and start fresh.

---

### Post by Ptah on 2006-12-16
I tried to reformat the disk but now is says that /dev/dev/sdb1 unknown files system.

Warning
Unable to detect filesystem! Possible reasons are;
The filesystem is damaged
The filesystem is unknown to gparted
There is no filesystem available (unformatted)

---

