---
title: "installing ubuntu damaged raid stripe"
date: 2008-01-20
forum: General Help
---

### Post by kossib on 2008-01-20
hey,

this night i tried installing ubuntu 7.10 on following configuration of disks

2 x 250 GB on SATA in RAID 0 (hda & hdb)
1 x 40 GB on ATA (hdc)
1 x 80 GB on ATA (hdd)

Motherboard is Gigabyte GA-035-DS3 so it isn't a "real" RAID controller, just a software one. 

I set it up to install in 40 GB one (hdc), i didn't understood what the option to modify my boot sector on hd0 was actually doing (I know it installs grub - i think)
but apparently it overwritten physical sectors of hda, not the sectors on combined RAID volume.
What i end up with, is inaccessible RAID setup (only the second disk is marked as "In RAID"), also booting to ubuntu is not possible - as system loader is not on the hdc (i tried to boot directly from it)

Is there a chance that the physical sectors were backed up, so they can be "put back" to the hda, so the RAID utility will treat the dis as "in RAID")

hope for a positive answer.

kossib

---

