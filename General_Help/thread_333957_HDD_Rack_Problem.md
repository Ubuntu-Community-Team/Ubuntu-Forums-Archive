---
title: "HDD Rack Problem"
date: 2007-01-08
forum: General Help
---

### Post by Magnes on 2007-01-08
I have HDD rack and three hard drives: first with Ubuntu, second and third I put in the HDD rack. I want to have both disks 2 and 3 partitions in fstab (so they would be mounted on the system start if the disk is present). But when I start the system (for example with disk 1 and disk 2) Ubuntu stops in the command line with "fsck.ext3 unable to resolve UUID" error. I must push CTRL+D then to continue. FAT32 partitions mount without problems. How to avoid this problem but still have the ability to automount the partitions?

The ext3 partitions I have in fstab writen like that:

UUID=21c472c1-c08d-45a5-8692-b4be0fba24e4 /media/mypartition ext3 defaults 0 1

---

### Post by dcstar on 2007-01-09
> **Magnes said:**
> I have HDD rack and three hard drives: first with Ubuntu, second and third I put in the HDD rack. I want to have both disks 2 and 3 partitions in fstab (so they would be mounted on the system start if the disk is present). But when I start the system (for example with disk 1 and disk 2) Ubuntu stops in the command line with "fsck.ext3 unable to resolve UUID" error. I must push CTRL+D then to continue. FAT32 partitions mount without problems. How to avoid this problem but still have the ability to automount the partitions?

The ext3 partitions I have in fstab writen like that:

UUID=21c472c1-c08d-45a5-8692-b4be0fba24e4 /media/mypartition ext3 defaults 0 1

Either manually replace the UUID portions with standard "/dev/hd" (or /sd) stuff, or install the pysdm package and let it do that for you.

You may still have to comment out the UUID lines if the drives do not exist on boot.

---

### Post by confused57 on 2007-01-09
Yes, you can just remove the UUID lines in fstab, see this guide:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

---

