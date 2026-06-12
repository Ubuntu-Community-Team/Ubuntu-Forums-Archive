---
title: "Small Root Partition, Can I switch /home to new partition?"
date: 2006-12-04
forum: General Help
---

### Post by mickbw on 2006-12-04
Hi,

I had a unpleasant weekend trying to install Edgy Ubuntu on an external USB drive.  The only way I was able to stop getting Error 18 was to use a very small / partition of only 3 GB and a swap of 1 GB.  I did this in the expectation I would be able to resize the sda1 partition to a larger size.  I was not able to do this because the extended partition was in the blocks directly next to the sda1 partition.  

So, I did what seemed to be the next best thing and expanded the extended partition to 50 GB and added a ext partition to fill up the extra space.  

My current fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         382     3068383+  83  Linux
/dev/sda2             383        6756    51199155    5  Extended
/dev/sda5             383         510     1028128+  82  Linux swap / Solaris
/dev/sda6             511        6756    50170963+  83  Linux
mick@mick-desktop:~$ 

```

Is there a way to switch over some of the folder from the sda drive to the new sda6 drive and make that the default location for apps and data?  

Everyone has been wonderful with their assistance to me in the last couple weeks.

Michael

---

