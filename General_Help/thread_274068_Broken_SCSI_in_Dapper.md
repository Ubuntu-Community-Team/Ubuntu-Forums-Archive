---
title: "Broken SCSI in Dapper"
date: 2006-10-09
forum: General Help
---

### Post by ktindle on 2006-10-09
I have an all-SCSI box- and I've hit something nasty in Dapper.

I had to edit the /etc/fstab to get rid of the udf filesystem option listed on my SCSI CD drive- yes, it is NOT a CD-DVD drive.  It will not play DVD- it never could- it isn't designed to do so.

That eliminated the hard lock-up when using a data CD- but the drive firmware locks up when you insert an audio CD.  Power must be removed from the drive to reset it- hard lock.

The SCSI ZIP 100 drive works, if you boot with media installed.  However, if you issue an eject command on the drive, while it does indeed eject, Dapper will freeze at some random point later.  The SCSI driver crashes, taking the hard disk drive with it.

The specific hardware-

ASUS Athlon XP system board
Adaptec 19160 SCSI card
Iomega SCSI ZIP 100 insider
Teac CD-532S CD-ROM drive

Dapper has some NASTY bugs in its Adaptec 19160 driver.  Real nasty.  I have no idea who to complain to, so you kind people here must endure this venting- and this warning.  Dapper assumes SCSI is dead.

---

