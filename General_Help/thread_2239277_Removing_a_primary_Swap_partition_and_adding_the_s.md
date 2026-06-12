---
title: "Removing a primary Swap partition and adding the space to an encrypted home folder"
date: 2014-08-12
forum: General Help
---

### Post by alireza-rafiee94 on 2014-08-12
I've switched from OpenSuse to Ubuntu. Hibernation works in OpenSuse but for some odd reason, it does not work in Ubuntu. Now I gave up enabling hibernation here, but I've partitioned a 17GB swap while installing the OS (I have 16GB of RAM). How can I remove it and allocate the space to my /home which is encrypted (also during the installation)?

---

### Post by TheFu on 2014-08-13
* make a know-you-can-recover backup of the system, data, everything you care about. Screwing with partitions - especially when encrypted - is dangerous.
* boot off a liveCD - partition work cannot be done if any of the partition are active.
* disable the swap
* delete the swap partition
* create a tiny swap - 2G is probably the right answer - that is NOT between the old swap and /home partitions
* add the freed storage to the /home partition.  This is only possible if they are next to each other physically, you are running LVM AND bother are either inside the extended partition or both are outside it.

Update:
* or just backup the encrypted partition, delete it, the swap, and create a new partition, encrypt it and restore the data into that new partition.

* This is one of the few times when seeing the partition layout in **gparted** as an image might be more helpful than **sudo parted -l** output and **df -h** - all 3 would be fantastic!

Have fun with this! The sense of accomplishment will be high AFTER.

---

### Post by oldfred on 2014-08-13
I do not know encryption, but issue does come up, so have a couple of links.

 Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
[http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

