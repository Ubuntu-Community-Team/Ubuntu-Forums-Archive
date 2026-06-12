---
title: "SATA drives changing dev assignments"
date: 2007-07-20
forum: General Help
---

### Post by glave on 2007-07-20
I have a server that has 2 promise 4 channel sata cards in it. I've been running raid5 and things went great up until recently. I upgraded to feisty, and now my drive assignments have been changing around on me like mad.
After doing some research, this fellow seemed to have a very simliar problem to mine: [http://www.linuxquestions.org/questions/showthread.php?t=563356](http://www.linuxquestions.org/questions/showthread.php?t=563356)

I have since created a udev map to all the correct UUIDs and things seem to boot up ok for the most part. The bad part is that different parts of the OS refer to the drives differently. Some pieces are refering to the drives as I have mapped them out, but others are refering to the drives as it thinks they should be. Now I have a failing drive in my array, and I can't figure out which one it is.

My system is setup like this:

1 ATA dvdrom on primary ide channel.
2 SATA 80g drives on mb sata channels (MB only has 2 total sata channels)
1 promise sata controller with 4 attached 300g hds
1 promise sata controller with 4 attached 500g hds

If I let the system assign as it seems fit, it *appears* that it wants to make the very last channel on the last sata controller /dev/sda. This seems exactly backwards of what I would normally expect. With the udev rules in place, cfdisk finds things as I would expect it to, but /proc/partitions is completely different. 

**How can I keep the drives uniformly refered to as the same assignments? Can I force it to make the mb onboard sata drives /dev/sda and /dev/sdb?  Is there no way I can figure out accurately which drive is giving me hassle without destroying my array (again)?**

Udev 70-local.rules
```
#-> for disks these rules will apply
#
#KERNEL=="sd*[!0-9]" means match drive named {sd[!=not 0-9]} only sda...sdz
#NAME="sda" set the name to SDA etc
#
#-> for partitions these rules will apply
#
#KERNEL=="sd*[0-9]" now match all other sda0..9 etc
#NAME="sda%n" %n will be the partition number
#
#
#Root drive 1
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_6L080M0_L217PATG", NAME="sda"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_6L080M0_L217PATG", NAME="sda%n"

#Root drive 2
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_6L080M0_L21BQKWG", NAME="sdb"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_6L080M0_L21BQKWG", NAME="sdb%n"

#300g 1
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_7L300S0_L60DB8RG", NAME="sdc"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_7L300S0_L60DB8RG", NAME="sdc%n"

#300g 2
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_7L300S0_L60DCJ8G", NAME="sdd"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_7L300S0_L60DCJ8G", NAME="sdd%n"

#300g 3
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_7L300S0_L60JCBAG", NAME="sde"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_7L300S0_L60JCBAG", NAME="sde%n"

#300g 4
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_6L300S0_L60NZFJG", NAME="sdf"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_Maxtor_6L300S0_L60NZFJG", NAME="sdf%n"

#500g 1
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG0WPC3", NAME="sdg"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG0WPC3", NAME="sdg%n"

#500g 2
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG0WH78", NAME="sdh"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG0WH78", NAME="sdh%n"

#500g 3
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG0WTGE", NAME="sdi"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG0WTGE", NAME="sdi%n"

#500g 4
KERNEL=="sd*[!0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG17M44", NAME="sdj"
KERNEL=="sd*[0-9]", ENV{ID_SERIAL}=="1ATA_ST3500630AS_5QG17M44", NAME="sdj%n"
```

---

### Post by glave on 2007-07-20
*Also, unfortunately none of my drives support SMART. :(

cat /proc/mdstat shows:
```
md3 : active raid5 sda1[0] sdh1[6] sdf1[5] sde1[4] sdd1[3] sdc1[2] sdb1[1]
      585954048 blocks level 5, 64k chunk, algorithm 2 [7/7] [UUUUUUU]

```

Which has the partitions COMPLETELY wrong. (Should be sdc1 sdd1 sde1 sdf1 sdg1 sdh1 sdj1, it did have sdi1 but it dropped it from a fail, so I added sdj1)

mdadm --detail /dev/md3 reports the partitions correctly though:
```

/dev/md3:
        Version : 00.90.03
  Creation Time : Sat Jul 14 08:57:56 2007
     Raid Level : raid5
     Array Size : 585954048 (558.81 GiB 600.02 GB)
    Device Size : 97659008 (93.13 GiB 100.00 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Fri Jul 20 09:32:13 2007
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 973bdb2d:506a7666:b4324d4e:0d4c5c1b
         Events : 0.828

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sde1
       3       8       49        3      active sync   /dev/sdf1
       4       8       65        4      active sync   /dev/sdg1
       5       8       81        5      active sync   /dev/sdh1
       6       8      113        6      active sync   /dev/sdj1

```

---

### Post by fjgaude on 2007-07-21
I have the same problem as you though I have only one raid5 array and one other drive. I reboot until the system notes the drives the way it did when I set them up in the array.

I wish there are others here that can be of more help. Help!

frank

---

### Post by fjgaude on 2007-07-24
See this post to understand how to solve this problem:

[http://ubuntuforums.org/showthread.php?t=444274&highlight=raid](http://ubuntuforums.org/showthread.php?t=444274&highlight=raid)

frank

---

