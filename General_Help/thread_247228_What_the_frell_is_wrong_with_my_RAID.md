---
title: "What the frell is wrong with my RAID?"
date: 2006-08-30
forum: General Help
---

### Post by cleentrax on 2006-08-30
OK, here's the setup:

4 320gb ATA drives in a RAID 5 (two on the motherboard IDE, two on a PCI-IDE CARD)
1 boot ATA drive

I have properly configured the 4 identical drives into a RAID-5 (/dev/md0) and mounted it as /storage. (listed in /etc/fstab).  I can transfer files to /storage. 

So here's the problem:

Every time I boot, the RAID does a resync, and crashes shortly after it's 90% finished resyncing. This crashes the whole system, which means my up time is never more than a couple of hours. Also, mdadm intermittently reports md0 as DeviceDisappeared, despite the fact that resync continues, and I can see and use the raid device. All four drives appear to be functioning properly, according to fdisk -l.

any thoughts? I'm going bonkers here!](*,)

---

