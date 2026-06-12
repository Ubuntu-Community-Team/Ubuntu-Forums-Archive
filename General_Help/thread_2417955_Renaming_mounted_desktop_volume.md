---
title: "Renaming mounted desktop volume"
date: 2019-04-29
forum: General Help
---

### Post by ubuntini2 on 2019-04-29
Just formatted a new external 1TB SSD as ext4 using gParted.

When it mounts on my desktop(Ubuntu) it simply shows as '1.0TB Volume'

1- How can I rename this to something more descriptive?
If I rightmouse click 'Rename' is greyed out.


It also shows up under a long and obscure mount point
ie
media/jim/1c12311a-1dd9-4718-befd-3f1ee0d14da11

Can this be shortened and-or renamed as well?

---

### Post by Dennis N on 2019-04-29
What you do is label the partition you have mounted. One tool to do that is called e2label.

example of use:
```
sudo e2label /dev/sdb1 mylabel

```change sdb1 to be the partition you want to label, and 'mylabel' to a name you want to appear (without spaces). It will probably take a reboot or at least log out and in to take effect.

---

### Post by TheFu on 2019-04-29
**gparted** can set labels on partitions too.
Or you can put the mount into the /etc/fstab file where you actually get to control everything and performance will be better than using some gvfs GUI thing to create a pseudo-mount.  google "ubuntu fstab" to find the guide for this.

Friends don't let friends use gvfs, except for very quick needs.  gfvs is not a kernel module it is FUSE and slow.

---

