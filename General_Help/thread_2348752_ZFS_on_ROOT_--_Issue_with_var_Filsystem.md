---
title: "ZFS on ROOT -- Issue with /var Filsystem"
date: 2017-01-06
forum: General Help
---

### Post by kreyszig2 on 2017-01-06
Hi,

So I did a ZFS on ROOT installation with 16.04 LTS and I have a issue with my ZFS tank/var filesystem. The ZFS filesystems I have include the following

tank/ROOT/default    /
tank/var                 /var
tank/var/tmp           /var/tmp
tank/var/log            /var/log
tank/var/spool         /var/spool

The issue I have is that tank/var does not mount at boot time because the system populates /var in tank/ROOT/default with a bunch a folders (lock, tmp, log, spool, etc) before tank/var gets mounted, so when the system attemps to mount tank/var, it fails because /var is not empty. I tried deleting everyting from /var on tank/ROOT/default but the issue reoccurs at every reboot. The only way to properly boot the system is to boot in recovery mode, do a "zfs umount -a", then "rm -rf /var" and "zfs mount -a". How can I ensure that tank/var gets mounted early enough as it should to prevent this issue?

Thanks!

---

### Post by kreyszig2 on 2017-01-09
Nobody knows what could be the issue? Thanks!

---

### Post by kevdog on 2017-01-09
No way of putting /var outside the zpool since in a different partition of disk?  ZFS root on linux kind of experimental at this time.

---

### Post by kreyszig2 on 2017-01-09
> **kevdog said:**
> No way of putting /var outside the zpool since in a different partition of disk?  ZFS root on linux kind of experimental at this time.

I would prefer avoiding that. There must be a way to ensure that all ZFS filesystems get mounted early enough so the directories do not get created before /var gets mounted, no?

---

