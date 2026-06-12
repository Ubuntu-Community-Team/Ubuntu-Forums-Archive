---
title: "gparted Fun (Apparently No partitions)"
date: 2014-05-14
forum: General Help
---

### Post by Trance_Kat on 2014-05-14
Hi All,
I recently (yesterday) became adventurous and decided to try and resize partitions on my system (/dev/sda).  I went from 4 partitions to 3.  After battling with 2 linux and 1 win7 paritions, and a mix of testdisk, gparted, and fdisk, I have the system mostly back to operational.  I have 1 linux partition and 1 windows partition working.

The issue I'm experiencing is that gparted seems to think that none of /dev/sda's space is allocated.  I'm hoping you may provide some insight and help with this.

output of sfdisk -l /dev/sda:
```

                                                                                                                                            
Disk /dev/sda: 14593 cylinders, 255 heads, 63 sectors/track                                                                                 
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0                                                                   
                                                                                                                                            
   Device Boot Start     End   #cyls    #blocks   Id  System                                                                                
/dev/sda1          0+   3857-   3858-  30983136+  83  Linux                                                                                 
/dev/sda2       3857+   7714-   3858-  30983168   83  Linux                                                                                 
/dev/sda3   *   7714+  14593-   6879-  55254016    7  HPFS/NTFS/exFAT                                                                       
/dev/sda4          0       -       0          0    0  Empty                                                                                 

```

output of fdisk -l /dev/sda
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total [COLOR=#ff0000]**234441648**[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8604958

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    61966335    30983136+  83  Linux
/dev/sda2        61968384   123934719    30983168   83  Linux
/dev/sda3   *   123934720   **[COLOR=#ff0000]234442751[/COLOR]**    55254016    7  HPFS/NTFS/exFAT

```
From the above, it looks like /dev/sda3 (my win7 partition[curiously set to book] is outside of bounds.  Is that something that needs to be fixed, and if yes, how does one go about fixing it please?)

output of parted /dev/sda
```

(parted) print partition
Error: Can't have a partition outside the disk!                           
(parted)

```

Here's what gparted shows:
[IMG]http://postimg.org/image/ry54x1evh/[/IMG]
[http://postimg.org/image/ry54x1evh/](http://postimg.org/image/ry54x1evh/)
using version 0.18.0

Any ideas of how to fix this please?

Thank you!



[B][SIZE=4]Found a solution!!!

[http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk](http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk)[/SIZE][/B]

---

