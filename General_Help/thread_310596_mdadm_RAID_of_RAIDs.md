---
title: "mdadm: RAID of RAIDs"
date: 2006-12-01
forum: General Help
---

### Post by bstephens on 2006-12-01
I'm trying to create a RAID5 array with three disks:

1: A 400GB disk
2: (Another) 400GB Disk
3: 2 x 200GB drives, which have been put into a RAID0

The array is created just fine; the problem is that when the machine is rebooted, no matter what I do, the RAID5 will start up in degraded mode, without using the RAID0 at all. My best guess was that they were being started up in the wrong order, and no amount of creating mdadm.conf files or making the RAID0 /dev/md0 and the RAID5 /dev/md1 has helped.

I'm pretty new to all this so I'm probably missing something obvious - I've tried this in both dapper and edgy and it isn't working on either (though edgy required a lot more effort to get it to this point)

I've run the following commands to create the array (on edgy) - the boot device /dev/sda is not involved in the raid

```

cfdisk /dev/sdb    (create new partitions, type FD)
cfdisk /dev/sdc
cfdisk /dev/hda
cfdisk /dev/hdb
mdadm --create /dev/md0 --auto=md --verbose --level=0 --raid-devices=2 /dev/hda1 /dev/hdb1
mdadm --create /dev/md1 --auto=md --verbose --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/md0
dpkg-reconfigure mdadm     (make it run on boot)

```

The array is just fine, and I can create a filesystem and mount it, until I reboot that is. Just for fun, here's my /etc/mdadm/mdadm.conf

```

DEVICE partitions
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=a01517ac:23ed2c29:1867650e:9c8c19c7
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=d97db4dc:08502920:90828f38:88fd7b46

```

Any help would be appreciated

---

