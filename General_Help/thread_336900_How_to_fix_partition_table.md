---
title: "How to fix partition table"
date: 2007-01-12
forum: General Help
---

### Post by g0nzo on 2007-01-12
Hi,

I'm not 100% sure, but probably installing Kubuntu messed up something with my partition table (or maybe it was done during resizing NTFS partition to make space for Kubuntu). Since then I had many problems with partitions - once I lost whole NTFS partition (recovered thanks to TestDisk), recently I lost my swap and ext3 partition when deleting NTFS partition.

This is what I get from TestDisk:
```

TestDisk 6.5, Data Recovery Utility, October 2006
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 310101 16 63
Current partition structure:
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 50028  15 63   50429169
 2 E extended LBA         50029   0 63 281743   1 63  233567776
 5 L HPFS - NTFS          50029   1  1 258852  15 63  210494529
   X extended             258856  14  1 279655   4 63   20964825
 6 L Linux                258856  15  1 279655   4 63   20964762

Warning: Bad starting head (CHS and LBA don't match)
   X extended             279655   5  1 281743   1 63    2104515

Warning: Bad ending head (CHS and LBA don't match)
 7 L Linux Swap           279655   6  1 281743   1 63    2104452

Warning: Bad starting head (CHS and LBA don't match)

```

Everything works correctly, but now I'd like to resize my system NTFS partition and I'm a little bit worried :) Do you know any tool (maybe TestDisk can do this) that will fix these errors? I know that it's not really related to Ubuntu, but maybe you can help.

Thanks in advance

---

### Post by ajgreeny on 2007-01-12
I've never used testdisk, but suggest you have a look at the live CD version of gparted:-
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It is a bit like partition magic in windows but runs quickly and easily from the CD so no partitions are mounted.  It can do all sorts of things that versions included in ubuntu can't so is worth having in your armoury at all times anyway.

Warning: Bad starting head (CHS and LBA don't match)
   X extended             279655   5  1 281743   1 63    2104515

Warning: Bad ending head (CHS and LBA don't match)
 7 L Linux Swap           279655   6  1 281743   1 63    2104452

Warning: Bad starting head (CHS and LBA don't match)
I'm not sure what these error messages really mean, but no doubt someone else will be able to help with that.

---

### Post by g0nzo on 2007-01-12
Thanks for reply.

I already tried Partition Magic 8.0 - it finds some errors, fixes them (at least it says so), but then another error appears (something about drive letters) and PM quits.

I also tried gparted from Ubuntu 6.10 live CD, but it didn't raised any errors and I couldn't find any options for analyzing and fixing partition table.

Does gparted live CD have some additional tools that could help?

---

### Post by ajgreeny on 2007-01-12
> **g0nzo said:**
> Thanks for reply.

I already tried Partition Magic 8.0 - it finds some errors, fixes them (at least it says so), but then another error appears (something about drive letters) and PM quits.

I also tried gparted from Ubuntu 6.10 live CD, but it didn't raised any errors and I couldn't find any options for analyzing and fixing partition table.

Does gparted live CD has some additional tools that could help?

Sorry I don't know about that.

---

