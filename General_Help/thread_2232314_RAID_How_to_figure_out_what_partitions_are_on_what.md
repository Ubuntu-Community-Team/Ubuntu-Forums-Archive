---
title: "RAID: How to figure out what partitions are on what drives?"
date: 2014-07-01
forum: General Help
---

### Post by FUBAR-BDHR on 2014-07-01
I've got kind of a weird hard drive/partition issue.  I reloaded an old p4 Novell server as a workstation to play around with.  The motherboard has an onboard Raid controller so I figured I'd do a mirror setup since I have 4 identical hard drives from the server.  For some strange reason the Raid controller only supports up to 2 non JBOD drives so I created 1 mirror group and left the other 2 drives as single drives.  Installation went fine and it's been running for a few weeks so I figured it was time to do a backup.  Went to partition one of the other hard drives but there seems to be no way of telling which drives are which.  I show all 4 drives, all 4 drives show identical information the only difference being the /dev/sda b c d.  All say they are Raid remembers with unknown contents.  I can't find any way of telling which 2 drives are the mirrored set and which 2 aren't.  Can't see any way to tell which partitions are on which drives although I picked the raid set when installing so they should be on that.  How do I tell what partitions are on what drives and which drives are the mirrored ones?  One the MB the mirrored drives are the masters on PATA controllers 2 and 3 and the other drives are on the slaves.

---

