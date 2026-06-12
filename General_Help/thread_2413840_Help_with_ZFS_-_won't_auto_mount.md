---
title: "Help with ZFS - won't auto mount"
date: 2019-03-02
forum: General Help
---

### Post by sf6 on 2019-03-02
Hello there,

in Ubuntu 18.10, I'm having trouble auto mounting my zfs pool.
Whenever I plug in the external SSD with the pool named "pool" I have to run

sudo zpool import -a

to get it to show up and be accessible.
Now I suspect it has something to do with me having created the pool using /dev/sdb as the device, but fdisk -l shows that right now it's actually /dev/sda.

How can I fix this?
Also concerning zfs in general, I have successfully created that pool, but I have not created a filesystem. However I managed to copy files onto that pool just fine. Is the filesystem automatically created when using a single disk?

Thanks.

---

