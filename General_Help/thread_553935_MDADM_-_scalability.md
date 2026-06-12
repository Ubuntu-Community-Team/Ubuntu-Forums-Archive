---
title: "MDADM - scalability?"
date: 2007-09-18
forum: General Help
---

### Post by Jeinhor on 2007-09-18
I have MDADM running with a RAID1-array (mirroring) with two disks (200 GB each).

Is it possible to extend this array, maybe convert it to RAID5 and add three more disks? Or convert it to RAID0+1 and add two more disks?

Of course I do not want the data to be erased...

Thanks in advance!

---

### Post by HavarN on 2008-06-15
Jepp, that should be possible:

Create a RAID5 array out of the two disks:
mdadm --create /dev/md0 --level=5 -n 2 /dev/sda1 /dev/sdb1

Then add a disk:
mdadm --add /dev/md0 /dev/sdc1
mdadm --grow /dev/md0 -n 3
fsck.ext3 -f /dev/md0
resize2fs /dev/md0

---

