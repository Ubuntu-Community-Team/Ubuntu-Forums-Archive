---
title: "USB floppy doesn't automount in Gutsy"
date: 2007-11-01
forum: General Help
---

### Post by boga on 2007-11-01
Hi,
It worked fine in Feisty, I just plugged an USB floppy drive with a disk inside and it mounted automatically. Now it doesn't work in Gutsy. The floppy is recognized properly and I can mount it manually. And this is not the problem [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025) since an USB flash drive automounts just fine and I've tried the suggested workaround for the problem with no success. dmesg | tail for the USB floppy:
```
[ 1112.348000] sd 6:0:0:0: [sdb] Write Protect is off
[ 1112.348000] sd 6:0:0:0: [sdb] Mode Sense: 00 46 94 00
[ 1112.348000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1112.476000] sd 6:0:0:0: [sdb] 2880 512-byte hardware sectors (1 MB)
[ 1112.508000] sd 6:0:0:0: [sdb] Write Protect is off
[ 1112.508000] sd 6:0:0:0: [sdb] Mode Sense: 00 46 94 00
[ 1112.508000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1112.508000]  sdb: unknown partition table
[ 1113.468000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1113.468000] sd 6:0:0:0: Attached scsi generic sg1 type 0

```
dmesg | tail for USB flash drive that automounts fine:
```
[ 1149.044000] sd 7:0:0:0: [sdb] Write Protect is off
[ 1149.044000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1149.044000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1149.068000] sd 7:0:0:0: [sdb] 512000 512-byte hardware sectors (262 MB)
[ 1149.076000] sd 7:0:0:0: [sdb] Write Protect is off
[ 1149.076000] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1149.076000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1149.076000]  sdb: sdb1
[ 1149.084000] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1149.084000] sd 7:0:0:0: Attached scsi generic sg1 type 0

```
Any ideas how to fix that?

---

