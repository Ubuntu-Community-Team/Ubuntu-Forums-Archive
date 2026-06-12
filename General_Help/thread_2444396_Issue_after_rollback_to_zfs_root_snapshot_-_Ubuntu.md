---
title: "Issue after rollback to zfs root snapshot - Ubuntu 20.04 ZFS bpool/rpool - apt broken"
date: 2020-05-29
forum: General Help
---

### Post by kneutron on 2020-05-29
--Ubuntu 20.04LTS zfs boot/root whole-disk installed on Samsung T5 external 500GB SSD, wanted to experiment with AWX (open-source Red Hat Tower) and Ansible and it broke after a reboot, taking Virtualbox 6.1 with it.

--Reverted to snapshot from the day before (just root, not userdata - and done as recommended at the GRUB prompt using the menu, not on live system) and APT broke trying to do an update-

```
Reading package lists... Error!
E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file - open (2: No such file or directory)
E: Problem opening
E: The package lists or status file could not be parsed or opened.
! Something failed! Code: 101 apt upgrade failed

[ ubu2004-zfs-t53 (scrn=2) ]
55 root ~ # ls -al /var/lib/dpkg/
total 12
drwxr-xr-x 2 root root 4 May 29 16:33 .
drwxr-xr-x 80 root root 80 May 14 20:55 ..
-rw-r----- 1 root root 0 May 29 16:33 lock
-rw-r----- 1 root root 0 May 29 16:33 lock-frontend
```

--I was able to restore /var/lib/dkpg from a tar backup archive that was on another machine in a zfs snapshot, since I have a separate "bkpcrit" bash file that I run just in case.

--Just a heads up to not rely solely on ZFS snapshots for backups - regularly backup critical system files to a separate disk and/or machine as well before doing apt upgrades... 20.04 is still in Beta as far as I'm concerned.

---

### Post by TheFu on 2020-05-29
> **kneutron said:**
>  --Just a heads up to not rely solely on ZFS snapshots for backups - regularly backup critical system files to a separate disk and/or machine as well before doing apt upgrades... 20.04 is still in Beta as far as I'm concerned.

The ZFS support in 20.04's installer is pretty clear.  ZFS use is EXPERIMENTAL.
Too bad the 20.04 release notes don't say this.  They don't say much about snap packages either, which has been causing thousands of people issues.

Snapshots on the same physical storage are never backups.  We all know that.

---

### Post by marcus292 on 2020-05-30
Yes its clear. But it needs some serious improvements. Many users are finding it tough to use [[COLOR=#000000][FONT=Arial]UPSers[/FONT][/COLOR]]("https://www.upsers.live/")

---

