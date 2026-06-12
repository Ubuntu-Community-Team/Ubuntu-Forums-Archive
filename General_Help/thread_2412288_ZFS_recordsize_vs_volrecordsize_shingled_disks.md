---
title: "ZFS recordsize vs volrecordsize shingled disks"
date: 2019-02-10
forum: General Help
---

### Post by mfarmwald on 2019-02-10
I use bunches of Seagate 8TB drives which are shingled. They work fine under Windows with caveats. Writing two files at the same time to the same disk results in horrible performance.
I'd like to switch from Windows to Ubuntu. I want to use ZFS with each drive being a separate Pool containing a single volume. The files being stored are very large and access is pretty much sequential read-mostly. For redundancy, I have two identical servers, so if I lose a drive on one, I just copy from the other.
As I understand ZFS, recordsize is just a suggestion, and it's not clear whether linux writes entire records at a time (which I think is best for shingled drives.)
I'd like to set volrecordsize, which seems to do more what I want (write and read big blocks, all of the time, even with simultaneous writes to the same hard drive but different files.)
If I create a pool with zpool, I can't set the volrecordsize, only recordsize. After the creation of a pool, volrecordsize is read-only. How do I create a volume with a large volrecordsize?
Alternatively, if someone has experience with shingled drives who can tell me the optimum settings for using them for media files, I would appreciate it.

---

