---
title: "Partition 2 does not start on physical sector boundary."
date: 2016-02-22
forum: General Help
---

### Post by Macamba on 2016-02-22
It seems my new system is a bit of a sick puppy. I have al kinds of errors to handle. So my apologies for all my posts. 

I have two hard drives in my new system. I kicked of one of the ATA connections on my motherboard. I had to connect HD1 (containing Windows 10) to ATA 2, and I think I connected HD2 (containging Ubuntu 14.4) to ATA 3.

I performed a ```

macamba@hermod:~$ sudo fdisk -l
...
Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xfd17e4d9

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdb1            2048   50000094   49998047  23,9G 83 Linux
/dev/sdb2        50001918 1953524589 1903522672 907,7G  5 Extended
/dev/sdb5        50001920  149999615   99997696  47,7G 83 Linux
/dev/sdb6       150001664  221999103   71997440  34,3G 82 Linux swap / Solaris
/dev/sdb7       222001152 1953524589 1731523438 825,7G 83 Linux

Partition 2 does not start on physical sector boundary.
```

I am a bit flustered with the last line. Do I "run in circles scream and shout" or is it not a problem?

---

### Post by oldfred on 2016-02-22
Extended partition does not matter. You do not write into extended partition.
What does matter is every other partition needs its start to be divisible by 8.

       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

