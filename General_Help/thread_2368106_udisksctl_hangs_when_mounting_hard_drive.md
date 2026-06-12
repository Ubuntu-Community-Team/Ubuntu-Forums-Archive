---
title: "udisksctl hangs when mounting hard drive"
date: 2017-08-07
forum: General Help
---

### Post by mberthelemy on 2017-08-07
Hi there,

I'm using Ubuntu 16.04 LTS. I have two drives:

/sda = 256Gb SSD
/sdb = 1Tb hard drive

I've been using the system for months with no problems. /sdb was set to automount using the instructions at: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Today however, /sdb does does mount properly on login. I can mount and unmount it manually using sudo mount /dev/sdb1 /media/1TBvolume and sudo umount /dev/sdb1

When I try to run udisksctl mount --block-device /dev/disk/by-uuid/<UUID> the process hangs and doesn't do anything. I can only get out using CTRL-C.

I'm not sure if the following is relevant:


[LIST]
[*]Yesterday I did an apt-get update / apt-get upgrade. In the process it required an update to the grub configuration. I followed the recommendations and made the changes to /sda1 only.
[*]I still have a directory: /media/<userID>/<UUID> - but it's inaccessible: You do not have the permissions necessary to view the contents of “<UUID>”.
[/LIST]

Any help very gratefully received!

Thanks,

Mark

---

