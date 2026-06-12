---
title: "Hello! Swap partition turning it self off"
date: 2021-03-28
forum: General Help
---

### Post by crackedmlv on 2021-03-28
My swap partition is turning off every time i reboot... And i don't want to every time go to gparted and turn it on! Please help!

---

### Post by CelticWarrior on 2021-03-28
Welcome.

If you changed the swap partition at some point or if it changed for some reason, you need to edit fstab.

---

### Post by crackedmlv on 2021-03-28
How to edit fstab i know how to: sudo gedit /etc/fstab but idk what to type!

---

### Post by CelticWarrior on 2021-03-28
```
sudo blkid
```
to find out which partition is currently the swap; compare with what you have in fstab.

---

### Post by TheFu on 2021-03-28
You need to enable the swap partition/file by creating a new line in the /etc/fstab. There are lots of how-to guides.  Google "ubuntu enable swap" and look for guides from domains with "ubuntu" in the domain name.  If you still need to know what to type - 
[LIST]
[*]post your fstab
[*]the output from **swapon -a** when it is working as you desire
[*]output from **blkid** that shows only the swap file/device you want used. Anything with 'loop' anywhere isn't needed nor wanted. loop devices have ZERO to do with storage and just add cruft.
[/LIST]

BTW, please don't edit system files with sudo gedit.  Use **sudoedit /etc/fstab** for safety.  If you want the editor used to be gedit, then set that as an environment variable.

---

### Post by crackedmlv on 2021-03-28
ouuput from sudo blkid: ```
/dev/nvme0n1p1: UUID="52B0-6B7C" TYPE="vfat" PARTUUID="2ae5add2-3b0f-4e0c-b1a1-7af3f773a975"
/dev/nvme0n1p2: UUID="5fef3b9c-2ead-4cfd-8af2-bda804fab3f6" UUID_SUB="376a4c04-80d8-4c56-9b50-850ef0539bb1" TYPE="btrfs" PARTUUID="0b5da7df-7273-4f37-a6cf-baa205a7fceb"
/dev/nvme0n1p3: UUID="2179f866-c16f-4fb7-be7e-8fb6d5e5e81f" UUID_SUB="288962e2-9ae9-486a-afb4-d182bd203871" TYPE="btrfs" PARTUUID="5c62a6b3-becd-4409-8ab8-fc02f81a5e28"
/dev/nvme0n1p4: LABEL="swap" UUID="39554f02-3d36-4f4b-b75b-e03028d5f22d" TYPE="swap" PARTUUID="2669d301-fe0c-4d7b-afee-ef954be320e2"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
```

FSTABFile:  
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=5fef3b9c-2ead-4cfd-8af2-bda804fab3f6 /               btrfs   noatime,defaults,subvol=@ 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=52B0-6B7C  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p3 during installation
UUID=2179f866-c16f-4fb7-be7e-8fb6d5e5e81f /home           btrfs   noatime,defaults,subvol=@home 0       2
/swapfile                                 none            swap    sw              0       0
```

---

### Post by deadflowr on 2021-03-28
You have no swap partition listed in fstab.
You have a swap labelled partition in the blkid output, but that is different than a swap file.
If you want the swap partition listed then add it like 
```
UUID=39554f02-3d36-4f4b-b75b-e03028d5f22d  none swap sw 0 0
```
you might want to disable the /swapfile while you're at it, just add a comment (#) to the beginning of it's line to disable it.

---

### Post by TheFu on 2021-03-28
Thanks deadflowr.

If the OP wants to see the swap in use, **swapon -s** will show it and which swap devices are currently being used. For example, 
```
$  swapon -s
Filename                                Type            Size    Used    Priority
/dev/dm-1                               partition       4300796 0       -2
```
This shows that I have a swap partition, of size: 4300796b - about 4.1GB.

The **free -hm** command can be used too:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       697Mi       1.1Gi       8.0Mi       2.0Gi       2.9Gi
**Swap:         4.1Gi          0B       4.1Gi**
```

Sizing of swap has been covered with multiple different opinions in these forums. About 8-12 months ago, there was a long thread about it.

---

### Post by HermanAB on 2021-03-28
Everything you never wanted to know about swap, is described in *man swapon*.  It is a very good man page and is well worth a read.

---

### Post by grahammechanical on 2021-03-28
According to this web site Ubuntu has not used a swap partition since Ubuntu 17.04. Ubuntu should be using a swap file.

[https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)

On my 20.04 system I see this

> graham@sdb1-sdb8:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:          3.7Gi       1.4Gi       562Mi        37Mi       1.7Gi       2.0Gi
Swap:            0B          0B          0B 


Is that because the system has enough memory capacity for its present tasks so that it does not need to allocate swap space? Would that printout indicate that swap is switched off? Perhaps what I am seeing and the OP is seeing is normal for present day Ubuntu. I have tried to find information on this but it all dates before the introduction of swap files by default. Oh, I still have what was the swap partition.

> graham@sdb1-sdb8:~$ sudo blkid
/dev/sdb5: UUID="7e924c2b-274c-478f-a340-76c1609ad29c" TYPE="swap" PARTUUID="0008e2df-05"

I imagine that the functioning of a swap file would be effected by the amount of hard disc space available. If the root partition is close to being full I imagine that a swap file might not be available. It all makes life interesting.

Regards

---

### Post by TheFu on 2021-03-28
swap file vs swap partition have pros and cons.  Some capabilities that swap partitions support are not supported by swap files. I suspect it is just because they are so new that all the different uses for swap haven't been fully fleshed out and some failure scenarios still exist.  

OTOH, if still using MSDOS partitioning in a dual-boot setup, the limited number of primary partitions (4) can make having a swap partition troublesome or impossible to setup.

I'm so used to allocating storage assuming swap is outside the / partition, so wasting 4+G of storage for swap really isn't in my planning.

---

