---
title: "rclone mount with fstab"
date: 2023-02-23
forum: General Help
---

### Post by zkab on 2023-02-23
I am trying to set up *rclone mount*.
Have installed & configured *rclone* and it works OK to my cloud storage *pcloud:*
That is I can access all my files at command level.
Problem is how to set up a mount with fstab.

The command
```
rclone mount  pcloud: /pcloud --vfs-cache-mode full --allow-other&
```
works OK and all my files in *pcloud:* show up in my file manager.

But adding in /etc/fstab following:
```
pcloud:  /pcloud rclone rw,noauto,nofail,_netdev,x-systemd.automount,args2env,vfs_cache_mode=full,config=/root/.config/rclone/rclone.conf,cache_dir=/var/cache/rclone 0 0
```
don't show any files in *pcloud:* with my file manager.

How can I change the line in /etc/fsta so it will work?

---

### Post by zkab on 2023-02-23
I solved the problem with *systemd mount units* and it worked.
Will not go fuhter with fstab ...

---

