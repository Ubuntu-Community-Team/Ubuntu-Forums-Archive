---
title: "Using the disks utility to create a disk image 13.04 Raring"
date: 2013-07-05
forum: General Help
---

### Post by apdobaj on 2013-07-05
Objective: Get a sector-by-sector clone of the hard drive for disaster recovery
What I've tried: systemrescuecd, clonezilla, native disks utility
Discussion: 
I'm attempting to find an intuitive and foolproof way to create a drive image for disaster recovery and it seems the disks utility would be useful for this purpose (unity -> disks -> select hard drive -> upper right gears icon -> create disk image). But whether I boot from a CD or from the hard drive I get a "Error opening device - error opening /dev/sda: Device or resource busy (udisks-error-quark,0)" error from the utility. I've verified that when booting from the CD that the hard drive and none of its partitions are mounted. The other solutions (or dd) would work, but this seems more elegant and simpler (which for me is important when done only once in a while).

---

### Post by Nathan_Stretch on 2014-04-09
> **apdobaj said:**
> Objective: Get a sector-by-sector clone of the hard drive for disaster recovery
What I've tried: systemrescuecd, clonezilla, native disks utility
Discussion: 
I'm attempting to find an intuitive and foolproof way to create a drive image for disaster recovery and it seems the disks utility would be useful for this purpose (unity -> disks -> select hard drive -> upper right gears icon -> create disk image). But whether I boot from a CD or from the hard drive I get a "Error opening device - error opening /dev/sda: Device or resource busy (udisks-error-quark,0)" error from the utility. I've verified that when booting from the CD that the hard drive and none of its partitions are mounted. The other solutions (or dd) would work, but this seems more elegant and simpler (which for me is important when done only once in a while).

I'm having *exactly *the same problem.  Can anyone help?  How is the device busy when we've booted from a livecd, and haven't mounted the drive?

---

