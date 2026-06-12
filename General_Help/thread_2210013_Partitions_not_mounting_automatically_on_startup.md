---
title: "Partitions not mounting automatically on startup"
date: 2014-03-08
forum: General Help
---

### Post by peyre on 2014-03-08
My desktop computer has an SSD for the system and a mechanical drive for file storage.  My laptop has a single drive with two partitions.  On both machines, when I boot up, the second drive/partition never mounts automatically--I have to click Places, click on the drive/partition, and click Mount.  I'm running Xubuntu 13.10 on both machines--32bit on the desktop, 64bit on the laptop.  Is there a way to get the second drive/partition to mount automatically?

---

### Post by papibe on 2014-03-08
Hi peyre.
You could create an entry in /etc/fstab . Here's a some documentation you may find useful:
[LIST]
[*][Introduction to fstab]("https://help.ubuntu.com/community/Fstab").
[*][Automatically Mount Partitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts")
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

P.S.: If you need more help to do this, please open a terminal run these commands, and post back its results (you can copy paste the results):
```
sudo fdisk -l

sudo blkid

cat /etc/fstab
```

---

### Post by peyre on 2014-03-08
Thanks!

Boy, I'm having trouble getting the syntax right.  It's just a simple second ext4 partition (I wanted to copy all my music files to the end of the hard drive, which should be the inside--therefore the slowest--part of the disk).  It's sda3, and this is the data you asked for:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00081f15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   443262975   221630464   83  Linux
/dev/sda2       484225022   488396799     2085889    5  Extended
/dev/sda3       443262976   484222975    20480000   83  Linux
/dev/sda5       484225024   488396799     2085888   82  Linux swap / Solaris

Partition table entries are not in disk order
leon@snowball:~$ sudo blkid
/dev/sda1: UUID="76d6d404-b082-4249-9c65-c409561c00d3" TYPE="ext4" 
/dev/sda3: UUID="e45a1229-2332-48ae-b10f-119b59d125aa" TYPE="ext4" 
/dev/sda5: UUID="4c71042d-af25-46fe-a0b5-5e5225c37649" TYPE="swap" 
leon@snowball:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=76d6d404-b082-4249-9c65-c409561c00d3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4c71042d-af25-46fe-a0b5-5e5225c37649 none            swap    sw              0       0
```

---

### Post by papibe on 2014-03-08
No problem.

Since you are mounting sda1 on / I am almost sure you want to automount sda3 (only other partition available anyway  ;) )

The safest way is to use sda3's id instead of mounting it directly to /dev/sda3:
```
dev/sda3: UUID="e45a1229-2332-48ae-b10f-119b59d125aa" TYPE="ext4" 
```
You need to decide where to mount it and create a mount point (basically a directory). For instance, if you want it on /data:
```
sudo mkdir /data
sudo chown youruser:youruser /data
```
(replace youruser for your actual username).

Finally, you can create the fstab entry at the end of the file:
```
# mount sda3 on /data
UUID="e45a1229-2332-48ae-b10f-119b59d125aa"  /data             ext4    defaults  0       2
```
Don't reboot just yet. Test if everything works by doing:
```
sudo mount -a
```
If the partition is mounted and you get no errors, reboot and double check if everything went OK.

Hope it helps. Let us know if that worked.
Regards.

---

### Post by mike555 on 2014-03-08
I use "disks", it lets you set mounting with a GUI , you might need to install it .

---

### Post by peyre on 2014-03-08
Hey that worked!  Thanks!  It's more of a workaround than a solution (ie, it didn't do quite what I was hoping), but it got the job done.

---

