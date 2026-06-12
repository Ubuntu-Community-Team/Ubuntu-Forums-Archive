---
title: "LVM vgextend without use of pvcreate"
date: 2024-06-25
forum: General Help
---

### Post by alexanderal on 2024-06-25
Hi, I added a new disk to my box and added it to my lvm with vgextend /dev/sdk normally i would do first a pvcreate /dev/sdk but i forgot. pvs -o+pv_used just shows:

PV         VG   Fmt  Attr PSize     PFree     Used  
....
  /dev/sdk   xxx  lvm2 a--  <1024.00g <1024.00g
....


is this ok? Or should i do a remove and start over?

regards,
Alexander

---

### Post by TheFu on 2024-06-25
PVs should always be pointed at partitions, not the full HDD.  There are a number of reasons for this that you can look up.  Your first step on any new HDD/SSD is to create a partition table, then create at least 1 partition, then mark that partition as an LVM type.

Extending VGs across multiple storage devices effectively doubles the likelihood of a failure losing all the data on both disks, unless you are going to make it a RAID1 setup using LVM-RAID.  I lost 80% of my data doing this a few decades ago.  I've since learned not to do it unless I have excellent backups to simple storage.

If you want better help, please post the exact commands used with the output from those commands shown, all wrapped in forum code-tags.  Without forum code-tags, columns are not retained here, so it is an important skill when asking for help.

---

