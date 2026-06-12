---
title: "Scanning Hard Drive"
date: 2014-09-21
forum: General Help
---

### Post by daniell59 on 2014-09-21
My hard drive is at least six years old. I would like to scan it for bad sectors. I would appreciate it if someone could explain to me how to do it in Ubuntu.

Ubuntu 14.04 32

Thanks

---

### Post by SuperFreak on 2014-09-21
> **daniell59 said:**
> My hard drive is at least six years old. I would like to scan it for bad sectors. I would appreciate it if someone could explain to me how to do it in Ubuntu.

Ubuntu 14.04 32

Thanks

You can use "Disks" program and within that check SMART attributes of HD

---

### Post by alex130 on 2014-09-21
This might help. [http://www.upubuntu.com/2012/12/check-for-bad-sectors-on.html](http://www.upubuntu.com/2012/12/check-for-bad-sectors-on.html)

---

### Post by grahammechanical on 2014-09-21
We can do it from the Grub boot menu. Select Recovery mode and at the recovery menu select fsck - check all file systems.

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

> [COLOR=#252525][FONT=sans-serif]Because running fsck to repair a file system which is mounted for read/write operations **can potentially cause severe **[/FONT][/COLOR]**[data corruption]("http://en.wikipedia.org/wiki/Data_corruption")**[COLOR=#252525][FONT=sans-serif]**/loss**, the _file system is normally checked while unmounted, mounted read-only, or with the system in a special maintenance mode_ that limits the risk of such damage. A [/FONT][/COLOR][journaling file system]("http://en.wikipedia.org/wiki/Journaling_file_system")[COLOR=#252525][FONT=sans-serif] is designed such that tools such as fsck do not need to be run after unclean shutdown (i.e. crash).[/FONT][/COLOR]

When we are at the recovery mode menu the file system is not yet mounted for read/write operations but for read only. Although we can change that by running some of the other options of the recovery menu.

Ubuntu by default use the Ext4 file system which is a journaling file system. 

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Regards.

---

### Post by tgalati4 on 2014-09-21
You can run badblocks:

Assuming the drive is /dev/sdb:

```
sudo fdisk -l
sudo badblocks /dev/sdb
```

Nothing returned is good.

To check the SMART parameters:

```
sudo smartctl -a /dev/sdb
```

---

