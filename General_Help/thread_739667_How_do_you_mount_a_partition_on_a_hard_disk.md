---
title: "How do you mount a partition on a hard disk?"
date: 2008-03-29
forum: General Help
---

### Post by 3pinner on 2008-03-29
I have used gparted to format some unallocated space on a hard disk.
Formatted as FAT32.
I will use this to store backups from Ubuntu.
gparted shows it as "unmounted"
How do I mount this new partition?
Thanks!

---

### Post by dcstar on 2008-03-29
> **3pinner said:**
> I have used gparted to format some unallocated space on a hard disk.
Formatted as FAT32.
I will use this to store backups from Ubuntu.
gparted shows it as "unmounted"
How do I mount this new partition?
Thanks!

Create a mountpoint (directory) for it, install the **pysdm** package and use that to do the job for you.

PS: FAT32 is probably the worst possible filesystem you could choose for something as important as a backup.

---

### Post by 3pinner on 2008-03-29
thanks for the tip on FAT32, I'll change it to Ext3.

---

### Post by 3pinner on 2008-03-30
I installed the pysdm package, configured the partition, reformatted it as ext 3, and mounted it.
When I reboot, I see it on my desktop, but I cannot access it.
Its  a permissions issue.
How can I change the permissions so it can be accessed by all users?
Thanks

---

