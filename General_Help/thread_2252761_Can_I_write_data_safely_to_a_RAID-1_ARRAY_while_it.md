---
title: "Can I write data safely to a RAID-1 ARRAY while it is resyncing?"
date: 2014-11-14
forum: General Help
---

### Post by nunecas123 on 2014-11-14
Will the files be in all drives on the array when the sync is complete? What if a disk fails while sync is in progress?

Thank you in advance.

---

### Post by TheFu on 2014-11-14
which RAID?  dmraid, software RAID, hw-RAID through a controller card?

I use softwareRAID and during a resync, progress can be monitored by watching /proc/mdstat.
Yes, you can write to the RAID metadevice why resync happens.  If 1 drive fails will you loose data? Well - it depends on which drive fails.  If the failed drive is the source of the resync - you are screwed.

This is why we always stress that RAID is not a substitute for backups.

---

