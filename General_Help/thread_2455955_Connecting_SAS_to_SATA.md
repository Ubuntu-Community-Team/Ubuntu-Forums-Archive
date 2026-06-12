---
title: "Connecting SAS to SATA"
date: 2020-12-31
forum: General Help
---

### Post by Phil Binner on 2020-12-31
I have my server operating well on both NFS and Samba, thanks to much help from this forum.  

My problem now is populating it.  To this end I followed advice and bought 3 second hand enterprise class 4Tb disks,  They have 22 pin data connectors, so the first problem is how to connect them to the motherboard.  I read severa\l articles, and it seems that SATA is IDE based, while SAS is Serial Attached SCSI.  According to my reading these should be incompatible, but there are no end of adapter cables offered which will allow me just to plug the SAS disks into SATA ports.  Rather than just trying this I'd like to get an idea as to whether it's likely to work.

What I'm intending to do with these disks is to twin two of them in a RAID 1 cluster, and have the third independent for nightly incremental backups.  The stand alone disk will not be raid.  I can then use other devices for longer term backups, particularly for more sensitive files, of which there are not so many.  With this in mind one other thing I'm investigating is using a RAID controller.  I have bought a second hand Dell E2K-UCS-51 RAID SAS SATA PCIe controller card.  I would like this to work, but it hasn't arrived yet.  It wasn't expensive so if it doesn't get used it won't be the end of the world.

As usual, any comments from this forum will be greedily leapt on (a bit of seasonal flavour there).

Thank you in advance.

---

