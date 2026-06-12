---
title: "LVM volume not mounted at startup"
date: 2014-06-29
forum: General Help
---

### Post by ionbasa on 2014-06-29
So I am running Ubuntu x64 14.04
I have a LVM volume named "mysql" with an ext4 file system at 100gb.
I can manually mount the volume using : ```
mount /dev/HAL-vg/mysql /var/lib/mysql/
```

I then proceeded to modify "/etc/fstab" using vim, I appended the following line to the file:
```
/dev/HAL-vg/mysql /var/lib/mysql ext4 noatime 0 2
```
But on startup the volume is no longer mounted and I have to run the mount command to this.

I believe this worked in earlier versions of Ubuntu. Has there been some change to fstab to mount LVM volumes? Or is this a bug?

---

### Post by ionbasa on 2014-06-29
OK, made a dumb mistake when editing fstab. Instead of "noatime" I accidentally made a typo and used "noauto".

---

