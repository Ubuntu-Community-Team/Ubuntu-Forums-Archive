---
title: "Changes in /dev/ for 6.10"
date: 2007-01-07
forum: General Help
---

### Post by millerdc on 2007-01-07
It seems some stuff like all the md* have been moved to /dev/.static/dev/ in 6.10. I figured this out after a new install. I wanted to setup a software RAID5 and found that mdadm is not installed by default anymore and the md* was moved. I kept getting file or directory not found for /dev/md0. So to create a new software RAID under 6.10 you need to use the new path. For example.

mdadm --create /dev/.static/dev/md0

Once mdadm does its thing md0 will show up under /dev/. Does anyone know way they changed this?

---

