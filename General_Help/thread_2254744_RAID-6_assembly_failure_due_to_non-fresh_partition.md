---
title: "RAID-6 assembly failure due to non-fresh partition"
date: 2014-11-29
forum: General Help
---

### Post by rbm0307 on 2014-11-29
Running an older version of Ubuntu (10.10) that has been very stable.  It's been configured with a software RAID-6 array consisting of 6 drives:
```
cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
# DEVICE /dev/sd*

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR <mail.addr>

# definitions of existing MD arrays

# This file was auto-generated on Sun, 14 Sep 2008 16:13:41 -0400
# UUID=614a41ae:61369299:f04c99b8:3fd94616
# by mkconf $Id$
ARRAY /dev/md0 level=raid6 num-devices=6 UUID=614a41ae:61369299:f04c99b8:3fd94616

# ARRAY /dev/md0 metadata=0.90 UUID=614a41ae:61369299:f04c99b8:3fd94616

```

The array will not assemble correctly.  Two drives are being kicked off the array because of non-fresh partition.  
```
cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid6 sda1[0] sde1[5] sdd1[4] sdc1[2]
      1953535744 blocks level 6, 64k chunk, algorithm 2 [6/4] [U_U_UU]

```

Extract from /var/log/messages below shows the reason for the two drives being rejected.  I don't believe this problem to be hardware related.:
```

Nov 29 16:41:34 MYTHbe kernel: [304303.349018] md: bind<sdb1>
Nov 29 16:41:34 MYTHbe kernel: [304303.349251] md: bind<sdc1>
Nov 29 16:41:34 MYTHbe kernel: [304303.350234] md: bind<sdf1>
Nov 29 16:41:34 MYTHbe kernel: [304303.351213] md: bind<sdd1>
Nov 29 16:41:34 MYTHbe kernel: [304303.351470] md: bind<sde1>
Nov 29 16:41:34 MYTHbe kernel: [304303.351658] md: bind<sda1>
Nov 29 16:41:34 MYTHbe kernel: [304303.351725] md: kicking non-fresh sdf1 from array!
Nov 29 16:41:34 MYTHbe kernel: [304303.351738] md: unbind<sdf1>
Nov 29 16:41:34 MYTHbe kernel: [304303.380207] md: export_rdev(sdf1)
Nov 29 16:41:34 MYTHbe kernel: [304303.380270] md: kicking non-fresh sdb1 from array!
Nov 29 16:41:34 MYTHbe kernel: [304303.380288] md: unbind<sdb1>
Nov 29 16:41:34 MYTHbe kernel: [304303.410131] md: export_rdev(sdb1)
Nov 29 16:41:34 MYTHbe kernel: [304303.423201] md/raid:md0: device sda1 operational as raid disk 0
Nov 29 16:41:34 MYTHbe kernel: [304303.423210] md/raid:md0: device sde1 operational as raid disk 5
Nov 29 16:41:34 MYTHbe kernel: [304303.423216] md/raid:md0: device sdd1 operational as raid disk 4
Nov 29 16:41:34 MYTHbe kernel: [304303.423222] md/raid:md0: device sdc1 operational as raid disk 2
Nov 29 16:41:34 MYTHbe kernel: [304303.424847] md/raid:md0: allocated 6386kB
Nov 29 16:41:34 MYTHbe kernel: [304303.426109] md0: detected capacity change from 0 to 2000420601856
Nov 29 16:41:34 MYTHbe kernel: [304303.426519]  md0: unknown partition table

```

Question is how to I freshen the drives to have them added to the array?

---

