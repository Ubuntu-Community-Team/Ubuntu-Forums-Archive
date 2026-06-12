---
title: "Sd Card Reader Only Working At Startup on Acer v5-171-6867 Running Ubuntu 14.04"
date: 2014-11-18
forum: General Help
---

### Post by juliusagustus on 2014-11-18
When I use the SD Card reader on my Acer v5-171-6867 running Ubuntu 14.04 I can only use it if I have a card inserted before I turn on my computer, other people seem to have a similar problem with either the same computer model or different computer models. So far I can't find any sort of real solution to this. Can anyone help?

---

### Post by cariboo on 2014-11-19
What does dmesg tell you when you insert the memory card? On my system it looks something like this:

```
[19992.710807] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[19992.712444] sd 4:0:0:0: Attached scsi generic sg1 type 0
[19993.365892] sd 4:0:0:0: [sdb] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
[19993.366990] sd 4:0:0:0: [sdb] Write Protect is off
[19993.367000] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[19993.370198] sd 4:0:0:0: [sdb] No Caching mode page found
[19993.370210] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[19993.405153]  sdb: sdb1
[19993.412997] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[19996.694401] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

```

---

