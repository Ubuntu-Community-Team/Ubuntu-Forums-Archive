---
title: "How to fix 240GB ext3 filesystem?"
date: 2006-10-19
forum: General Help
---

### Post by jcsston on 2006-10-19
Hi,
I have a RAID-5 with three 120GB disks making a single 240GB ext3 formatted partition. For some reason the ext3 journal has a failed.

Here are the entries in my syslog relating to the failure,
```
Oct 18 18:10:45 slota kernel: [275808.463351] attempt to access beyond end of device
Oct 18 18:10:45 slota kernel: [275808.463358] md0: rw=1, want=0, limit=468872704
Oct 18 18:10:45 slota kernel: [275808.502330] Aborting journal on device md0.
Oct 18 18:18:28 slota kernel: [276271.463446] ext3_abort called.
Oct 18 18:18:28 slota kernel: [276271.479070] EXT3-fs error (device md0): ext3_journal_start_sb: Detected aborted journal
Oct 18 18:18:28 slota kernel: [276271.511434] Remounting filesystem read-only
Oct 18 20:19:52 slota kernel: [283553.274282] EXT3-fs error (device md0): ext3_readdir: bad entry in directory #12861442: rec_len %% 4 != 0 - offset=56, inode=12861452, rec_len=12589, name_len=21
```
I've tried running fsck but it uses a huge amount of memory, 2.5GB+ before it runs out of swap space.

Is there any way to recover the filesystem and data?

Thanks,
Jory

---

