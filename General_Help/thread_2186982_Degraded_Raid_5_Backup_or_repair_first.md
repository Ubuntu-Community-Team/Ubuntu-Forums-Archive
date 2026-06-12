---
title: "Degraded Raid 5: Backup or repair first?"
date: 2013-11-10
forum: General Help
---

### Post by mail3 on 2013-11-10
Dear all, this is my first post, so hello everybody (I have been a reader of this forum for a long time already without ever registering).

I wanted to have some opinions on my problem:
On my 3 drive RAID 5 (Software RAID with mdadm 3x2TB disks, 12.04 Server), one drive has crashed yesterday (hardware fail, drive is not even recognized any more).
The RAID is degraded but still working.

Is it safer to repair the raid first (replace the missing disk) or back it up on my 4TB backup disk while it is still degraded?
In other words: Is an additional failure more likely during repairing the Raid or during backing up the data in degraded mode?

---

### Post by TheFu on 2013-11-10
The answer depends on how good/old the backups are.  I would have a backup from 2am the day of the failure, so I would fix the RAID disk.

What failed on the drive?  A cable, controller, port or the HDD itself?  Based on that answer ... I might have a different answer.

IMHO, Backups always, always, always trump RAID. Always ...... always.  Since RAID is NOT a backup.  RAID is only for high-availability.

---

### Post by mail3 on 2013-11-10
Thanks for your answer.
The drive itself failed (around 3 years of age). It is making loud noises while starting up and is not recognized any more. Seagate will replace it.

My backup is not too bad, i have got about 99% backed up. I keep the backup on a disk at my parents house, just to physically separate it, therefore i am not doing backups every day.

I guess the risk is about the same and should be very low, since in both cases the two healthy disks just have to read out the data written on them?

---

### Post by SeijiSensei on 2013-11-10
Back up first and worry about the array afterwards.

---

### Post by mail3 on 2013-11-20
Thanks, that's exactly what i have done. Backup went fine and also the rebuild of the thrid drive went thru without any problems. Rebuilding took longer, so i guess backing up was less risky.

Another question arose while rebuilding: I realized that my RAID is built up by the whole drives and not the partitions on them, i.e. sda, sdb and sdc and not sda1, sdb1 and sdc1. Are there any disadvantages? Should i change that?

---

### Post by TheFu on 2013-11-20
There are advantages to each method.  The main reason to partition is so that we don't forget there is data on the drive when put into any other non-RAID system.  There are other reasons - google will find many discussions about this topic.

If the drives will **never** be used in any other system (which is never a safe bet in a home environment), then I'd lean towards not partitioning.

Dealers choice.

---

