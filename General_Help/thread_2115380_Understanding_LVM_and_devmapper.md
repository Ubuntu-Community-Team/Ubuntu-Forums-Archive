---
title: "Understanding LVM and /dev/mapper"
date: 2013-02-12
forum: General Help
---

### Post by AnalBeard on 2013-02-12
Ok, so I use LVM at work on CentOS but I can't quite get my head round how Ubuntu implements it.

Firstly, I'm running Ubuntu Server 12.04 and booting from a compact flash card. I did a default LVM install, but forgot to disable swap. I'll post the output of the various settings:

```

root@sepulveda:/dev# df -h
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/sepulveda-root  1.6G  1.4G   78M  95% /
udev                        960M  4.0K  960M   1% /dev
tmpfs                       388M  312K  388M   1% /run
none                        5.0M     0  5.0M   0% /run/lock
none                        970M  4.0K  970M   1% /run/shm
/dev/sda1                   228M   28M  189M  13% /boot
sepulveda.tank              5.4T  2.0T  3.4T  38% /mnt/tank
/home/simon/.Private        1.6G  1.4G   78M  95% /home/simon

```
```

root@sepulveda:/dev# pvs
  PV         VG        Fmt  Attr PSize PFree 
  /dev/sda5  sepulveda lvm2 a-   3.49g 52.00m

```
```

root@sepulveda:/dev# vgs
  VG        #PV #LV #SN Attr   VSize VFree 
  sepulveda   1   2   0 wz--n- 3.49g 52.00m

```
```

root@sepulveda:/dev# lvs
  LV     VG        Attr   LSize Origin Snap%  Move Log Copy%  Convert
  root   sepulveda -wi-ao 1.51g                                      
  swap_1 sepulveda -wi-ao 1.93g 

```
```

root@sepulveda:/dev# cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/dm-2                               partition	2027516	0	-1

```
```

root@sepulveda:/dev# cat /etc/fstab
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sepulveda-root /               ext4    errors=remount-ro 0       1
UUID=cd50e8a1-40cc-4e18-a785-bb2df0e71514 /boot           ext2    defaults        0       2
/dev/mapper/sepulveda-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

Now this is where I started to get confused. df shows / mounted from '/dev/mapper/sepulveda-root'. However, lvs shows the root LVM partition as being named 'sepulveda'. Under CentOS (6), LVM partitions are easy enough to understand, they come under '/dev/vol_group_name/lvm_name'. Making an assumption, I presume /dev/mapper maps to another udev node elsewhere? 

Basically, where I'm going with this is this: if I were to turn swap off, what device node should I be pointing the command at?

Can I run the following instead?

```

 sudo swapoff -U <uuid>

```

```

root@sepulveda:/dev# blkid
*snip*
/dev/mapper/cryptswap1: UUID="1c21bd8a-5cca-4e5d-a230-57d736c540f3" TYPE="swap" 
*snip*

```


Edit: I should say, the whole reason for this post is that due to my swap partition taking up over half the available space, I need to bin the swap partition and extend the root partition to use the whole drive instead.


Further edit: I ran swapoff with the UUID given by blkid and it has indeed disabled swap. I'd still like to understand how Ubuntu uses /dev/mapper though if anyone would like to explain?

---

