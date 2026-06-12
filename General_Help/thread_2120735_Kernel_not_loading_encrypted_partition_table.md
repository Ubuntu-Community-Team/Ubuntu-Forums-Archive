---
title: "Kernel not loading encrypted partition table"
date: 2013-02-27
forum: General Help
---

### Post by gkaragoulis on 2013-02-27
I have a 1TB backup drive that I want split into 2x 500GB encrypted partitions.  I am using cryptsetup luksFormat to create an encrypted drive, upon which I wrote the partition table.  Note that this is different than creating 2x partitions on the raw disk and then encrypting them both separately.  _In my scenario the partition table itself is encrypted._

The problem occurs during boot.  cryptdisks_start successfully finds and starts my crypt disk, and it maps it to "/dev/mapper/backup_main" for example.  But now I need it to read the partition table on this encrypted device.  The boot sequence stops at this point for user intervention because fstab can't auto-mount the partitions that don't exist yet.  After the computer boots I have to execute:

```
kpartx -a /dev/mapper/backup_main
```

...which adds the mapped partition devices to /dev/mapper/backup_main1 and /dev/mapper/backup_main2.  The question is, how do I force the kernel to read the partition table after cryptdisks_start, but before fstab tries to auto-mount my drives?

My workaround that I thought of involves not auto-starting the crypt drive, and running a custom init script which starts it manually and forces the kernel to read its partition table after it's started.  Is there a more proper way to do this?

---

