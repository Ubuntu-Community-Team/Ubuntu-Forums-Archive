---
title: "Extra MDADM superblock showing up"
date: 2007-10-16
forum: General Help
---

### Post by ultralame on 2007-10-16
(I am writing this away from my system, so please excuse the slight lack of info).

I have a raid5 array with 6 drives in a 4+1+1 (spare) arrangement.  A couple of those disks were previously part of another 2+1 array.

Each drive is partitioned to give me two mountable volumes, /dev/md0 and /dev/md1.

I have been running Edgy for a while, with no problems.  I upgraded to Feisty the other day and the system was working fine.  But when I rebooted there was an error and it appears that the system had started the array using an old superblock.

When I boot into an EDGY live CD, apt-get install mdadm and run:
> mdadm -Ebsc partitions

I get this:
> ARRAY /dev/md0 level=raid5 num-devices=3 UUID=X spares=1
ARRAY /dev/md0 level=raid5 num-devices=5 UUID=Y
ARRAY /dev/md1 level=raid5 num-devices=5 UUID=Z
(I have substituted out the UUIDs here).

It appears that the first entry is from the earlier array.
If I manually start the array using
> mdadm -Ac partitions
everything starts correctly.  I am able to mount, R/W and run fsck.  So it does not start the old array.

When I boot normally, the old array IS started, and begins to sync.

How can I find and get rid of the old 3-drive entry?

---

