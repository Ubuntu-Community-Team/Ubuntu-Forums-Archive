---
title: "Help! Can't format drives that used to be part of an md array!"
date: 2008-04-22
forum: General Help
---

### Post by msodrew on 2008-04-22
So I've got four 750GB hdd's that are supposed to be used for a software RAID5 array via mdadm. I set them up once and then accidently totally nuked the OS afterwards (doing other things, not important).

Anyhow, here it is plain and simple: Screw the old array, I just want to make a new one. I know the steps are

1. Create single partitions on all drives for the raid array
2. Format the partitions to ext3
3. Set the RAID flag
4. Do mdadm commmands

Problem is, it fails on step 2... whenever I go
```
# mkfs.ext3 /dev/sdb1 
```

It says

```
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
```

I know what you're thinking. NO, the filesystems are not mounted (for every single drive: sdb, sdc, sdd, sde). NO, there is no entry for them in /etc/fstab. NO, umount /dev/sd<##> does nothing.

I can't seem to force it to reformat the drive! I believe its because linux still thinks its part of the old array to some degree given dmesg:

```
# dmesg | grep sde
[   49.450206] sd 5:0:0:0: [sde] 1465149168 512-byte hardware sectors (750156 MB)
[   49.450217] sd 5:0:0:0: [sde] Write Protect is off
[   49.450219] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   49.450237] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.450276] sd 5:0:0:0: [sde] 1465149168 512-byte hardware sectors (750156 MB)
[   49.450286] sd 5:0:0:0: [sde] Write Protect is off
[   49.450289] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   49.450306] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.450309]  sde: sde1
[   49.454584] sd 5:0:0:0: [sde] Attached SCSI disk
[   49.652767] md: bind<sde1>
[   49.726186] md: unbind<sde1>
[   49.726191] md: export_rdev(sde1)
[   49.753264] md: bind<sde1>
```

and it's the same for sdb1, sdc1, and sdd1... how do I prevent it from thinking its part of an array on startup?

---

### Post by WhiteHorse on 2010-02-05
Probably a reference to your disks in mdadm.conf

sudo vi /etc/mdadm/mdadm.conf

---

### Post by falconindy on 2010-02-05
+1 for the idea above, but...

Skip step 2. You don't need to format them, because the partition table will be rewritten when the RAID device is created.

---

