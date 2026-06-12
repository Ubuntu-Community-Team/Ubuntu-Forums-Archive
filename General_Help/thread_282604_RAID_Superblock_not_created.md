---
title: "RAID Superblock not created"
date: 2006-10-23
forum: General Help
---

### Post by bforbes on 2006-10-23
I used mdadm to create a RAID1 array with two drives, but no RAID superblock appears to have been written. By that I mean: 

mdadm -E /dev/md0

complains about not finding a superblock. However, the array can be mounted and used. The downside is that I need to explicitly describe the array in /etc/mdadm.conf, as opposed to letting mdadm work it out automatically.

Does anyone know how to force the superblock to be written?

---

