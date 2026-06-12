---
title: "very large disk in ubuntu 7.04 x86"
date: 2007-09-21
forum: General Help
---

### Post by rofa on 2007-09-21
Have a large RAID array on a hardware controller.

Ubuntu 7.04 64bit and Fedora 7 detects it fine.

But this is what I get with the Ubuntu 7.04 x86 installation (kernel 2.6.22).

```


/var/log/messages

[sda] Very big device. Trying to use READ CAPACITY(16).
[sda] 10742792192 512-byte hardware sectors (5500310 MB)
[sda] Write Protect is off
[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sda: unknown partition table
sd 9:0:0:0: [sda] Attached SCSI disk
sd 9:0:0:0: Attached scsi generic sg0 type 0

fdisk -l

Disk /dev/sda: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


```

Anyone know how to fix this?

---

