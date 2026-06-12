---
title: "Secondary HDD Access/NTFS/Partition"
date: 2008-05-30
forum: General Help
---

### Post by FMDragon on 2008-05-30
Let me describe the set up first.
I've got two hard drives, A and B. A has two partitions, one for Vista formatted in NTFS, the other for Gutsy, formatted in ext3. B is just one single partition, formatted in NTFS, and used just for data/media.
So I blew away my Vista partition (ditched it for an XP virtual machine) and now drive B is not showing up mounted on the desktop. In my /media folder there is a folder there with hdb1 but it is empty. 
Does anyone have any advice? Thanks.

---

### Post by EXCiD3 on 2008-05-31
Was your drive disconnected safely the last time you used it (either via the icon in tray or by a regular shutdown with no interruptions)? Sometimes this prevents my NTFS partitions from mounting.

Can you post the output of this:```
sudo cat /etc/fstab
```
(this just lists the drives that are automounted upon booting)

---

