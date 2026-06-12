---
title: "Mount Commands"
date: 2008-01-28
forum: General Help
---

### Post by Graham1 on 2008-01-28
Hi

When mounting partitions in fstab, can "/dev/hda?" be used rather than "UUID=xxxxx"? Also, does the spacing between <file system>, <mount point>, <type>, etc matter?

:)

---

### Post by taurus on 2008-01-28
It works either you use /dev/sdaX or UUID.  And by the way, you can look up the UUID in /dev/disk/by-uuid.

```
ls -la /dev/disk/by-uuid
```
And as long as there is a space, either single or multiple, it should be good in /etc/fstab.

Example:
```
/dev/sdaX /media/sdaX ext3 defaults 0 1
-or-
/dev/sdaX     /media/sdaX     ext3     defaults     0     1
```

---

### Post by Graham1 on 2008-01-28
I'll use hda? then as it's simpler and alot easier to use :). I have a FAT32 partition that I would like to add to fstab. Somehow it is being mounted (to Media) but it is not listed under fstab. Are there any particular settings I should add?

:)

---

