---
title: "permisson problem"
date: 2008-05-12
forum: General Help
---

### Post by HappyFeet on 2008-05-12
i have an ext3 partion that i cant access. when i open it, there's a lost and found folder. i tried chown and changing my fstab.

here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1f86dde7-2830-40c4-bc47-af31ec0acfba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
**UUID=c0295d3b-6c97-3bb5-fe53-36c2c332829c /media/sda5     ext3    auto,rw,exec,user    0   0**
# /dev/sda3
UUID=af9ed2a7-f8fe-4296-910b-47c8a3290262 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

does the highlighted line look ok?

---

### Post by HappyFeet on 2008-05-12
i need to bump this because im installing for someone and they need their computer back soon. thanks for any help.

---

### Post by bodhi.zazen on 2008-05-12
The lost and found folder is normal and part of the file system. Leave it alone (do not delete it or change permissions)

Your fstab entry looks fine.

---

### Post by HappyFeet on 2008-05-15
> **bodhi.zazen said:**
> The lost and found folder is normal and part of the file system. Leave it alone (do not delete it or change permissions)

Your fstab entry looks fine.

but there is 3 gigs of data i need to access on that partition. when i open the "storage" partition, all i see is a lost and found folder. how can i access the files i need?

---

### Post by bodhi.zazen on 2008-05-15
From your description the partition is empty.

Are you sure this is the correct partition ?

Are you sure you did not format it ?

Mount the partition and lets see the output of :

```
df -f | grep sda5
```*assuming it is mounted at /media/sda5

---

