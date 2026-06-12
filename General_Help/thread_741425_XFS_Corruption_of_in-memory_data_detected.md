---
title: "XFS: Corruption of in-memory data detected"
date: 2008-03-31
forum: General Help
---

### Post by Alun on 2008-03-31
Hi,

I am getting errors on my XFS mount every few hours. The mount is an mdadm RAID 1 array. Here are some details of the error:

From /var/log/syslog:
```
Mar 31 00:30:01 ubuntu /USR/SBIN/CRON[21249]: (root) CMD (/usr/bin/rsnapshot hourly)
Mar 31 00:31:34 ubuntu kernel: [40934.016175] Filesystem "dm-0": XFS internal error xfs_trans_cancel at line 1132 of file /build/bu
ildd/linux-source-2.6.22-2.6.22/fs/xfs/xfs_trans.c.  Caller 0xffffffff8898a6d5
Mar 31 00:31:34 ubuntu kernel: [40934.016189] 
Mar 31 00:31:34 ubuntu kernel: [40934.016190] Call Trace:
Mar 31 00:31:34 ubuntu kernel: [40934.016321]  [_end+137510510/2130324728] :xfs:xfs_trans_cancel+0x116/0x140
Mar 31 00:31:34 ubuntu kernel: [40934.016350]  [_end+137548749/2130324728] :xfs:xfs_link+0x295/0x490
Mar 31 00:31:34 ubuntu kernel: [40934.016372]  [_end+137351625/2130324728] :xfs:xfs_dir_lookup+0x161/0x170
Mar 31 00:31:34 ubuntu kernel: [40934.016406]  [_end+137595013/2130324728] :xfs:xfs_vn_link+0x5d/0xd0
Mar 31 00:31:34 ubuntu kernel: [40934.016417]  [__up_read+33/176] __up_read+0x21/0xb0
Mar 31 00:31:34 ubuntu kernel: [40934.016439]  [_end+137513555/2130324728] :xfs:xfs_trans_unlocked_item+0x3b/0x60
Mar 31 00:31:34 ubuntu kernel: [40934.016446]  [__up_read+33/176] __up_read+0x21/0xb0Mar 31 00:31:34 ubuntu kernel: [40934.016466]  [_end+137513555/2130324728] :xfs:xfs_trans_unlocked_item+0x3b/0x60
Mar 31 00:31:34 ubuntu kernel: [40934.016487]  [_end+137535858/2130324728] :xfs:xfs_access+0x4a/0x60Mar 31 00:31:34 ubuntu kernel: [40934.016502]  [vfs_link+360/448] vfs_link+0x168/0x1c0
Mar 31 00:31:34 ubuntu kernel: [40934.016511]  [sys_linkat+350/400] sys_linkat+0x15e/0x190
Mar 31 00:31:34 ubuntu kernel: [40934.016519]  [cp_new_stat+231/256] cp_new_stat+0xe7/0x100Mar 31 00:31:34 ubuntu kernel: [40934.016537]  [sys_newlstat+54/80] sys_newlstat+0x36/0x50
Mar 31 00:31:34 ubuntu kernel: [40934.016554]  [system_call+126/131] system_call+0x7e/0x83
Mar 31 00:31:34 ubuntu kernel: [40934.016568] 
Mar 31 00:31:34 ubuntu kernel: [40934.016574] xfs_force_shutdown(dm-0,0x8) called from line 1133 of file /build/buildd/linux-source
-2.6.22-2.6.22/fs/xfs/xfs_trans.c.  Return address = 0xffffffff88981194
Mar 31 00:31:34 ubuntu kernel: [40934.025753] Filesystem "dm-0": Corruption of in-memory data detected.  Shutting down filesystem: 
dm-0
Mar 31 00:31:34 ubuntu kernel: [40934.025763] Please umount the filesystem, and rectify the problem(s)
```


and then when i umount and then mount again:
```
Mar 31 23:53:28 ubuntu kernel: [88105.600195] Filesystem "dm-0": Disabling barriers, not supported by the underlying device
Mar 31 23:53:28 ubuntu kernel: [88105.604769] XFS mounting filesystem dm-0
Mar 31 23:53:28 ubuntu kernel: [88105.666359] Starting XFS recovery on filesystem: dm-0 (logdev: internal)
Mar 31 23:53:53 ubuntu kernel: [88118.193764] Ending XFS recovery on filesystem: dm-0 (logdev: internal)
```

It seemed to occur while rsnapshot was running. Does anyone have any ideas what could be causing this?

Thanks,
Alun

---

### Post by fjgaude on 2008-03-31
Could it be a bad memory chip?

---

