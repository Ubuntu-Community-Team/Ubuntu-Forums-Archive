---
title: "Partition table screwed?"
date: 2006-09-09
forum: General Help
---

### Post by chrisccoulson on 2006-09-09
I was adding an ext3 logical partition in some unallocated space earlier ,using GParted on the Dapper live CD. After it finished, it told me that all of the space on my drive was unallocated. This obviously made me panic a bit.

However, when I rebooted my machine, it seems to be ok. However, GParted still tells me that my whole drive is unallocated.

The output of fdisk -l /dev/mapper/nvidia_dgcadeeg gives:

```
omitting empty partition (9)

Disk /dev/mapper/nvidia_dgcadeeg: 500.1 GB, 500118697984 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_dgcadeeg1               1       19581   157284351    b  W95 FAT32
/dev/mapper/nvidia_dgcadeeg2           19582       60665   330007230    5  Extended
/dev/mapper/nvidia_dgcadeeg3           60666       60796     1052257+  83  Linux
/dev/mapper/nvidia_dgcadeeg4           60797       60802       48195   83  Linux
/dev/mapper/nvidia_dgcadeeg5           19582       22192    20972826   83  Linux
/dev/mapper/nvidia_dgcadeeg6           22193       41773   157284351   83  Linux
/dev/mapper/nvidia_dgcadeeg7           41774       42034     2096451   82  Linux swap / Solaris
/dev/mapper/nvidia_dgcadeeg8           42035       56880   119250463+  83  Linux

```

Could anyone shed any light on to what I might have done? Cheers

---

