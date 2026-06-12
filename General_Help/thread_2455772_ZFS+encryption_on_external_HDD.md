---
title: "ZFS+encryption on external HDD"
date: 2020-12-27
forum: General Help
---

### Post by macnoobgets on 2020-12-27
Hi everyone. I installed Ubuntu 20.10 with **ZFS and whole-disk encryption** (using the standard installer). Next I **cloned **(simple with dd) this disk with fresh installation (lets say it's disk A)  to disk B and booted from disk B. Everything is fine. But I can't find a way to mount disk A disk from gnome-disks utility running under the system booted from disk B (as well as I can't mount B on system running from A). It seems Ubuntu doesn't yet support mounting zfs+encryption external drives on working system (which was booted from another zfs+encryption drive).

The error is: **unknown filesystem type 'zfs_member'.**
The screenshot is attached.

Part#1: 1.0 MB Unknown
Part#2: 538 MB FAT **< this mounts, but contains only 'EFI' and 'grub' dirs**
Part#3: 2.1 GB Unknown
Part#4: 2.1 GB zfs_member - rpool **< can't mount, unknown filesystem type 'zfs_member'.**
Part#5: 500 GB zfs_member - bpool  **< can't mount, unknown filesystem type 'zfs_member'.**

Thank you all and happy new year!
PS: Ubuntu RULEZ

---

### Post by TheFu on 2020-12-30
Did you change the UUIDs after cloning?
Are the poolnames different?

I don't know, but those things would be confusing to the OS and ZFS, yes?

---

