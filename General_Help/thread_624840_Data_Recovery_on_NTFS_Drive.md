---
title: "Data Recovery on NTFS Drive"
date: 2007-11-27
forum: General Help
---

### Post by renzokuken on 2007-11-27
hi all, sorry if this is not in the best place but here goes anyway.

my brother recently tried to reformat/reinstall windows on his PC to get it working speedily again.

he had XP installed on a SATA drive and an IDE drive as a Storage drive. (his computer comes with a recovery partition .... i hate those things....)

he used the CDs he burnt from recovery partition to reformat and restore XP. Now this is where it went wrong, it initially started reformatting his IDE storage drive (master/slave/IDE over SATA etc). i managed to stop the recovery process at 1% realising what was happening. we disconnected the storage drive and managed to successfully reinstall XP on the original SATA drive.

however, on reconnecting the IDE storage drive, it appears to be blank and Explorer lists the partitions as if the recovery CD had repartitoned it.

he had a lot of data on that drive, photos, dissertation etc.......if i'm thinking right, less than a minute would not be sufficient time to wipe that drive, and all that has happened is that the partition table has been rewritten and so the data is still there, just not viewable with the current partition table?

am i correct in this thinking? and if so, what can we do about it? he desperately wants that data back.

thanks

---

### Post by az on 2007-11-27
> **renzokuken said:**
> 

am i correct in this thinking? and if so, what can we do about it? he desperately wants that data back.

thanks

I would think there is a high probability that 99 percent of the data is still there.  I think there is a low probability that your filsystem index is intact and you will not be able to rescue the filesystem as a whole.  You need to carve out the files from the block device.

Use foremost or photorec.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

or

[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

---

