---
title: "Setting up Ubuntu after fedora .. Disk partition can't be formated"
date: 2018-03-24
forum: General Help
---

### Post by a7med95 on 2018-03-24
Hey,

I am new to Linux.
I downloaded fedora and looks like i missed up my disk partitions.

I notice that when i switched to Ubuntu.
Some of fedora partition can't be removed.

My Disk looks like: show by lsblk command:
```
NAME             MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sdb                8:16   0 119,2G  0 disk  
&#9492;&#9472;sdb1             8:17   0 119,2G  0 part  
  &#9500;&#9472;fedora-home  253:1    0 900,8G  0 lvm   /home
  &#9492;&#9472;fedora-swap  253:2    0   8,8G  0 lvm   
    &#9492;&#9472;cryptswap1 253:3    0   8,8G  0 crypt [SWAP]
sr0               11:0    1  1024M  0 rom   
sdc                8:32   1  14,9G  0 disk  
&#9492;&#9472;sdc1             8:33   1  14,9G  0 part  /media/a7med/Jesusa <3
sda                8:0    0 931,5G  0 disk  
&#9500;&#9472;sda2             8:2    0     1G  0 part  /media/a7med/f53b40bc-2a6f-4089-89e4
&#9500;&#9472;sda3             8:3    0 930,3G  0 part  
&#9474; &#9500;&#9472;fedora-home  253:1    0 900,8G  0 lvm   /home
&#9474; &#9492;&#9472;fedora-root  253:0    0   140G  0 lvm   /
&#9492;&#9472;sda1             8:1    0   200M  0 part  /boot/efi

```

Tried to use the the disk manager in ubuntu to manage the disk and remove all fedora related disks (partitions).
But, no success .. Here is the error that shows up:
[IMG]https://s14.postimg.org/q7zbj1ebl/Screenshot_from_2018-03-24_14-30-23.png[/IMG]

Any suggestion for what to do ?
Thanks in advance !!

---

### Post by oldfred on 2018-03-24
Fedora uses LVM by default. Many that dual boot just use a standard ext4 partition rather than the LVM.

Is your system also RAID as you show /home in both sda1 and sdb3 and same size. Or did you span drives with the LVM, with part of /home on one drive and part on other drive. LVM does provide that feature.
You many have to use LVM tools to remove the LVM volumes, then you can use gparted to remove partitions the volumes were in.

[https://www.howtoforge.com/linux_lvm_p6](https://www.howtoforge.com/linux_lvm_p6)

---

