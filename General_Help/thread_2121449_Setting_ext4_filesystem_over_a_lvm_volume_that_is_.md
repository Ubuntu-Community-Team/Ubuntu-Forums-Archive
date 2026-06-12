---
title: "Setting ext4 filesystem over a lvm volume that is stripped across 4 drives"
date: 2013-03-01
forum: General Help
---

### Post by gilmcgrath on 2013-03-01
I have created a logical volume using the following commands on ubuntu 12.04:

pvcreate  /dev/vde  /dev/vdf  /dev/vdg  /dev/vdh
vgcreate db_vol_grp  /dev/vde  /dev/vdf  /dev/vdg  /dev/vdh
lvcreate -i 4 -L 100G db_vol_grp

The lvcreate reported that the strip size as 65 kB.

I would like to create a ext4 file system on the logical volume /dev/db_vol_grp/lvol0.

The actual disks are 4 iscsi end points to an netapps appliance.

I have a question:

What options should I use to create the ext4 file system to ensure I optimize the stripped volume?

I am confused about the stride and strip width options.

Any help or insight would be appreciated.

---

