---
title: "ZFS does not start on physical sector boundary."
date: 2015-09-22
forum: General Help
---

### Post by benjamin25 on 2015-09-22
Hello all,

I recently setup ZFS and am happy so far, but when I am looking at the drives and the partitions I get two problems. The first is when I use ```
sudo disk -l
``` I get one partition on each of the six disk in my zpool, as you would expect. However, each one also prints [HTML]Partition 1 does not start on physical sector boundary[/HTML]. I was wondering if this is a problem? I created my pool with ```
ashift=12
``` because, as you would expect, my disks have 4096 physical sectors. I have heard having the partitions not aligned can impact performance, though I haven't noticed so far.

My second problem is when is use ```
lsblk
``` instead of ```
fdisk
``` I get a partition of 8M on each zpool disk in addition to the actual data partition of 2.7TB (3Tb drives). I assume this is the reason I am getting the physical sector issue, but I don't understand why ZFS is not using the whole disk. I have just used the following command to create the pool: ```
[COLOR=#263034]sudo zpool create -o ashift=12 data raidz2 sda sdb sdc sdd sde sdf[/COLOR]
```

Thank you in advance for any help.

---

