---
title: "Rsync Command"
date: 2014-04-17
forum: General Help
---

### Post by kevin44 on 2014-04-17
Hi,

I am trying to rsync on a machine running 64 bit Ubuntu 12.04.4 LTS.  
Background Information:  The source of the data is on /mnt/driveA while the destination of the data is /mnt/driveB.  /mnt/driveA is a drobo that is using drobo's version of hardware RAID 6.  The destination of the data is a 1 TB hard-drive.

I run the following command to do the rsync:  rsync -auv /mnt/driveA/ /mnt/driveB/

The rsync completes with no errors.  The issue I have is that after the rsync completed I ran the "df -lah" command and it shows that /mnt/driveA has 645G of data on it while /mnt/driveB has 642G of data on it

My questions are:

1) Why don't /mnt/driveA and /mnt/driveB have the exact same amount of data on them after the rsync?

2) Can I modify the rsync command somehow so I can get that 3 GB of data copied from /mnt/driveA to /mnt/driveB?


Thanks in advanced to anyone who can help me with this.

---

### Post by rbmorse on 2014-04-17
I'm wondering if what you're seeing is just the difference in slack space between a RAID volume and a single disk.

---

### Post by davea42 on 2014-04-18
From [https://en.wikipedia.org/wiki/Standard_RAID_levels](https://en.wikipedia.org/wiki/Standard_RAID_levels) you will see (at a high level) what various
RAID levels are and do.  Raid 6 involves (among other things) extra parity blocks.
When you copy out of RAID onto a non-RAID disk all the raid parity is left behind.
It is meta-data and has no place in the ordinary non-RAID version.  So expect
the non-RAID version to be smaller than RAID.

Actually any copy of a group of files can wind up taking (in total) a different amount of space than
the original did.  It depends on the particular file systems and
how the file systems deal with small files and even on the order a file system sees the files when creating them.
The total difference in space taken will ordinarily be quite small (as a percentage).

---

