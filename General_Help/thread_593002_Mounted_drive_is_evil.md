---
title: "Mounted drive is evil"
date: 2007-10-26
forum: General Help
---

### Post by AndAy224 on 2007-10-26
When I attempt to execute anything on this drive it says 'Permission Denied', even when I sudo it, I'm just plain out of ideas so I thought I'd ask you guys for help. Below is my fstab for the drive.

/dev/sdb1       /mnt/etudes/    ext3    rw,user,noatime 0       1

Here is the drive permissions from /mnt/

total 4
drwxr-xr-x 7 anday root 4096 2007-10-26 18:31 etudes


Any Ideas? :/

---

### Post by AndAy224 on 2007-10-26
Stupid mistake on my part.

Add exec to fstab works fine now.

---

