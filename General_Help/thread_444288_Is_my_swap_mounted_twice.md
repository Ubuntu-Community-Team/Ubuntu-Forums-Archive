---
title: "Is my swap mounted twice?"
date: 2007-05-15
forum: General Help
---

### Post by akudewan on 2007-05-15
I had made a swap partition of about 666 MB, but when I checked /proc/meminfo, it shows me:
```

SwapTotal:     1365504 kB
SwapFree:      1299004 kB

```

Even gkrellm, and other monitoring software show my swap as 1334MB.

When I did cat /proc/swaps, I got this:
```

Filename                                Type            Size    Used    Priority
/dev/sdb3                               partition       682752  66492   -1
/dev/mapper/sdb3                        partition       682752  0       -2

```

Is my swap mounted twice or something ? :confused:

---

### Post by Rizado on 2007-05-15
It seem so. There shouldn't be any in /dev/mapper as far as I know.
/dev/mapper is where my raid array appears. :-s

---

### Post by taurus on 2007-05-15
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
free
```

---

### Post by sandman55 on 2007-05-15
Boot with your live CD and check it out with gparted

---

### Post by NoNo_231 on 2007-05-15
I see the same problem  in the desktop and laptop that I have - both updated from 6.10->7.04
$The results of the desktop are
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       1662688 234944  -1
/dev/mapper/hda5                        partition       1662688 0       -2

$sudo fdisk -l
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4791    38483676   83  Linux
/dev/hda2            4792        4998     1662727+   5  Extended
/dev/hda5            4792        4998     1662696   82  Linux swap / Solaris

$cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=0b0807e9-c115-4994-bcbe-fe1b32b62956 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 none swap sw 0 0
UUID=dc8fff3e-9ac3-4181-a39e-c0a35f60778b none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

$free
             total       used       free     shared    buffers     cached
Mem:        775688     766116       9572          0       7016     202684
-/+ buffers/cache:     556416     219272
Swap:      3325376     235020    3090356

Thanx

---

### Post by Delkster on 2007-05-15
I had a similar problem and posted about it in [this thread](http://ubuntuforums.org/showthread.php?t=400203). If I remember correctly, I got rid of it by uninstalling LVM and EVMS (and possibly mdadm) packages which I don't need because I don't use logical volume managers, RAID or other such magic.

It's a little worrying that the problem seems to keep popping up, though. I hope it doesn't cause risk of data corruption. I got it solved on my part (completely, as far as I can tell) by getting rid of the aforementioned services but it doesn't sound good that the system can be put into that state by the upgrade.

---

### Post by NoNo_231 on 2007-05-15
Thanx Delkster,

I removed evms in both computers and they are running smoothly right now :)

Thanx again.

---

### Post by akudewan on 2007-05-15
Yes, removing evms did the trick

---

### Post by drf666 on 2007-05-15
Had the same problem...

All my drives were mounted as /dev/mapper/sd*, plus the gnome-search tool showed my drive as "DEV" instead of the normal "FileSystem"

I removed LVM, EVMS and MDADM to restore normal setup. Thanks for the solution!

Could this be related to my upgrade path? Dapper -> Edgy -> Feisty
Also I had to answer questions about MD something in the last upgrade.

---

