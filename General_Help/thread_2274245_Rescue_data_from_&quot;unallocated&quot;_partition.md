---
title: "Rescue data from &quot;unallocated&quot; partition"
date: 2015-04-18
forum: General Help
---

### Post by umlumbi on 2015-04-18
While installing Windows I've somehow managed to damage the file system. The partition where Ubuntu 14.04 was installed (sda6, somehow under sda4)  shows as unallocated on gparted and I can't access its data. I gave up on the other operation system an had to install another Ubuntu in the first partitions. I wish to recover the data in the sda4/sda6;

fdisk says it "does not start on physical sector boundary".

I have looked for similar problems but none of the solutions worked for me. Is there a way to recover its data? if so, how?

Thank you for your time.
 
```
:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x6b2eec54


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20482047    10240000   82  Linux swap / Solaris
/dev/sda2   *    20482048   409599999   194558976   83  Linux
/dev/sda3       409600000  1458175999   524288000    7  HPFS/NTFS/exFAT
/dev/sda4      1458178046  1953523711   247672833    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1933527040  1953523711     9998336   82  Linux swap / Solaris



```

---

### Post by Mark Phelps on 2015-04-19
> I have looked for similar problems but none of the solutions worked for me. Not very useful information!  How do we know what you've already tried so we don't mention the same thing again?

Try using Testdisk: [http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery]("http://ubuntuforums.org/showthread.php?t=387922&highlight=data+recovery")

---

