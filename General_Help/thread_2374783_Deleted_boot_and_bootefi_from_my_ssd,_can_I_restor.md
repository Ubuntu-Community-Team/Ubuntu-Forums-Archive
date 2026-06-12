---
title: "Deleted /boot and /boot/efi from my ssd, can I restore them?"
date: 2017-10-19
forum: General Help
---

### Post by xplodeme2 on 2017-10-19
I accidentally removed my /boot and /boot/efi partitions from my pcie ssd managed by lvm. 

Is there any way to restore them?

This is the output from lsblk before my accident:
olof@synd:~/$ lsblk 
NAME                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1                      259:0    0 372.6G  0 disk 
&#9500;&#9472;nvme0n1p3                  259:3    0 371.6G  0 part 
&#9474; &#9500;&#9472;ubuntu--gnome--vg-swap_1 253:1    0  31.9G  0 lvm  [SWAP]
&#9474; &#9492;&#9472;ubuntu--gnome--vg-root   253:0    0 339.7G  0 lvm  /
&#9500;&#9472;nvme0n1p1                  259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2                  259:2    0   488M  0 part /boot

Now it looks like this:
olof@synd:~/$ lsblk
NAME                         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1                      259:0    0 372.6G  0 disk 
&#9492;&#9472;nvme0n1p3                  259:3    0 371.6G  0 part 
  &#9500;&#9472;ubuntu--gnome--vg-swap_1 253:1    0  31.9G  0 lvm  [SWAP]
  &#9492;&#9472;ubuntu--gnome--vg-root   253:0    0 339.7G  0 lvm  /

olof@synd:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.10
Release:        16.10
Codename:       yakkety




Any help is appreciated.

Cheers

---

### Post by oldfred on 2017-10-19
If you manually recreate ESP (FAT32 with boot flag) & ext2 boot partition and run Boot-Repair it may work. You may need to mount / and look at fstab to to see UUID of ESP & /boot and update those first to UUID of new partitions.

But Boot-Repair may need you to manually mount the LVM especially if encrypted first. It needs to be able to mount ESP, /boot & / partitions. It often gets confused with LVM & RAID as both use /mapper and it uses fstab to find partitions.
Boot-Repair has options to reinstall grub & latest kernel in its advanced mode screens.

Boot-Repair's advanced screens.
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

