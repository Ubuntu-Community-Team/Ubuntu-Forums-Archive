---
title: "unknown filesystem type 'LVM2_member'"
date: 2018-01-18
forum: General Help
---

### Post by David4321 on 2018-01-18
I'm on 17.10 artful, trying to mount drive that still has 16.04 xenial on it from an external drive bay. (my old OS drive)

I can see the drive in Drives as /dev/sdf2, but it does not appear in file manager as other drives do from bay. I also tried plugging it in internally.

I tried this:
```
$ sudo mkdir /media/aurora
$ sudo mount /dev/sdf2 /media/aurora
mount: /media/aurora: unknown filesystem type 'LVM2_member'.
$ sudo apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version (2.02.168-2ubuntu3).
```
How can I mount this drive?

---

### Post by strixtux on 2018-01-19
When you attach your drive via USB - can you make it visible with disks?
If yes, you maybe able to mount it manually. works for me sometimes.

---

### Post by Dennis N on 2018-01-19
sdf2 is apparently an lvm physical partition. It doesn't have a file system you can mount. See display below from my computer. 

```
[dmn@Roxanne ~]$ lsblk -o NAME,TYPE,FSTYPE
NAME                       TYPE FSTYPE
sdb                        disk 
&#9500;&#9472;sdb1                     part ext4
&#9500;&#9472;sdb3                     part LVM2_member
&#9474; &#9492;&#9472;os_vg-ubuntu_1710_lv   lvm  ext4
&#9500;&#9472;sdb5                     part swap
&#9500;&#9472;sdb6                     part LVM2_member
&#9474; &#9500;&#9472;os_vg-mint_18_mate     lvm  ext4
&#9474; &#9492;&#9472;os_vg-u_1710_mate      lvm  ext4
&#9500;&#9472;sdb7                     part ext4
&#9500;&#9472;sdb8                     part ext4
&#9500;&#9472;sdb9                     part ext4

```
Instead, you would mount the lvm devices (TYPE=lvm). For example, I cannot mount sdb3 or sdb6, but can mount os_vg-ubuntu_1710_lv with:
```
sudo mount /dev/os_vg/ubuntu_1710_lv /mnt/tmp
```

---

