---
title: "/etc/fstab boot hangs at Create Volatile Files and Directories"
date: 2019-01-29
forum: General Help
---

### Post by jimrph62 on 2019-01-29
Ubuntu Server 18.x LTS

After Calibre hung system following large import, powered off. All boot attempts since hang at Create Volatile Files and Directories. Research indicates it involves the /etc/fstab file. The contents are listed below.

UUID=e6bce2cc-b91d-11e8-93b8-54bf6467cad5 / ext4 defaults 0 0
/swap.img    none        swap    sw    0    0
/dev/disk/by-uuid/f38bd955-fbd7-487f-8a81-d21542bd440f /mnt/disks/zmovies auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/sdc1 /mnt/disks/ztv ext4 auto 0 2
/dev/disk/by-id/wwn-0x5000c500b12eb540-part1 /mnt/wwn-0x5000c500b12eb540-part1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/wwn-0x5000c500b127d339-part1 /mnt/wwn-0x5000cca22ece10c6-part1 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0

This is beyond my ability to solve, at least quickly. I would appreciate any assistance.

Jim

---

### Post by TheFu on 2019-01-29
Is the disk full?  Probably need to boot from alternate media, like a flash drive to check that, assuming that "Recovery mode" doesn't work from Grub.

---

