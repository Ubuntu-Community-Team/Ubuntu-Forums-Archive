---
title: "Write Permissions for RAID"
date: 2007-05-05
forum: General Help
---

### Post by drscotty on 2007-05-05
ARRGGG!!!  I have wasted hours on this seemingly simple problem:

I cannot write to the RAID 1 device I just created, because the permissions are 755, and I cannot chmod, chown, or chgrp the mount point, or any directories under the mount point.   WHY???

I have two SATA drives, and partitioned them as type 'fd', 'Linux raid autodetect'.

I then ran 'mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sd[cd]1'

This worked fine, and I could then mount the new device.   I created a mount point '/repository' with the permissions set to 775, and the owner and group set to 'root' and 'users' respectfully.

When I mount '/dev/md0' to '/repository', the permissions are changed to 755, and the user and group is 'root' and 'root'.   Even as root, I cannot change any of the permission, owner, or group settings.

The one thing I tried was to add the line, 'CREATE group=users mode=0660' to my /etc/mdadm/mdadm.conf file, but that seems to have had no effect.

So, the long and short of this is that only root can write to the RAID, and this is not acceptable.  I know there must be a simple answer, but I have searched these and other forums, and have not found it.   Please help if you can!   I am going nuts!   

FYI, here is my /etc/mdadm/mdadm.conf file:

DEVICE partitions
CREATE group=users mode=0660 
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=feaca4b3:5d2e395c:d3876495:b22ebf65
MAILADDR root

Thanks,

Scott

---

