---
title: "Confusion with SSD partition capacity after installation - 20.04"
date: 2021-07-05
forum: General Help
---

### Post by freeflyjohn on 2021-07-05
I recently installed Ubuntu Server 20.04 onto a 1TB SSD, but I am very confused by the space used and free space available.

During installation I configured the SSD as follows:


[LIST]
[*]Partition for /root, 128 GB , ext4
[*]Partition for /boot, 1GB, ext4
[*]Partition for /home, rest of volume, ext4
[*]Partition for swap, 16 GB , swap
[/LIST]



However, when looking at the capacity for root and home they are different

/root shows the capacity is 210.3GB but I expected the capacity not be 128GB as defined in the installation ?


/home shows there is only 176.3GB of free space with 2.7GB used, but the partition was set to rest of volume which was 786.509GB.  So where has the rest of the capacity gone ?

---

### Post by freeflyjohn on 2021-07-05
This is what's displayed in Disks

Im confused by partition 3 as I thought it should be ext4 but it says its LVM ?

---

### Post by ajgreeny on 2021-07-05
Please see I have removed the huge images from your posts in this thread and replaced with thumbnails.
Please in future use the attachment facility, the paperclip icon in the toolbar of the Replay To Thread dialogue window.

---

### Post by oldfred on 2021-07-05
You chose LVM - logical volume management, not standard partitions. Your / & /home then are in the LVM. 
Often used with servers.

LVM Advantages/Disadvantages Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://ubuntuforums.org/showthread.php?t=2456746](https://ubuntuforums.org/showthread.php?t=2456746)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by ActionParsnip on 2021-07-05
LVM is great and very flexible. Worth investigating. If you have managed storage before then it's no different. Disk space is in a pool and assigned out to file systems as needed to grow them. If you want more space, add a new disk to the pool the distribute the new capacity out as necessary.

---

