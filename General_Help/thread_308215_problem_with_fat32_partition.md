---
title: "problem with fat32 partition"
date: 2006-11-27
forum: General Help
---

### Post by ruialexbarbosa on 2006-11-27
Hi,

my system (edgy) won't boot up. Checking the partitions with livecd my fat32 partition has a Danger sign, and when I double click it it says "unable to read the contents of this filesystem! Because of this some operations may be unavailable. Did you install the correct plugin for this filesystem?"

Could this have something to do with it? (my system hangs at boot and it says it's checking filesystem)

thanks for any help

---

### Post by shin on 2006-11-27
Do you have some custom kernel? Fat32 support is built in (I think) in ubuntu's kernels from repo.

About checking FS - this is normal for ext3 partition. When you hard reboot your machine, it forces consistency check. Also by default ext3 is checked every 30 mounts. Give it some time, especially if you got large disk. But actually in my opinion it would be better to format your partition to some better FS for home desktop, e.g. jfs or xfs.

---

### Post by jdegreeley on 2007-07-21
I had the same problem (only with Feisty) and a reboot fixed it.

Jay

---

### Post by stchman on 2007-07-22
> **ruialexbarbosa said:**
> Hi,

my system (edgy) won't boot up. Checking the partitions with livecd my fat32 partition has a Danger sign, and when I double click it it says "unable to read the contents of this filesystem! Because of this some operations may be unavailable. Did you install the correct plugin for this filesystem?"

Could this have something to do with it? (my system hangs at boot and it says it's checking filesystem)

thanks for any help

Do you have your file system encrypted on FAT32?

---

