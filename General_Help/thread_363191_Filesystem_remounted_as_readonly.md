---
title: "Filesystem remounted as readonly"
date: 2007-02-16
forum: General Help
---

### Post by erland on 2007-02-16
My MythTV media center box remounted the main video directory as readonly in the middle of the night. This has also happened one time before a few months back.

/var/log/syslog when the problem occured says:
```

Feb 15 04:35:59 htpclin kernel: [18086072.712000] EXT3-fs error (device sda7): ext3_free_blocks_sb: bit already cleared for block 84170518
Feb 15 04:35:59 htpclin kernel: [18086072.712000] Aborting journal on device sda7.
Feb 15 04:35:59 htpclin kernel: [18086072.736000] ext3_abort called.
Feb 15 04:35:59 htpclin kernel: [18086072.740000] EXT3-fs error (device sda7): ext3_journal_start_sb: Detected aborted journal
Feb 15 04:35:59 htpclin kernel: [18086072.740000] Remounting filesystem read-only
Feb 15 04:35:59 htpclin kernel: [18086072.740000] EXT3-fs error (device sda7) in ext3_reserve_inode_write: Journal has aborted
Feb 15 04:35:59 htpclin kernel: [18086072.740000] EXT3-fs error (device sda7) in ext3_truncate: Journal has aborted
Feb 15 04:35:59 htpclin kernel: [18086072.740000] EXT3-fs error (device sda7) in ext3_reserve_inode_write: Journal has aborted
Feb 15 04:35:59 htpclin kernel: [18086072.740000] EXT3-fs error (device sda7) in ext3_orphan_del: Journal has aborted
Feb 15 04:35:59 htpclin kernel: [18086072.740000] EXT3-fs error (device sda7) in ext3_reserve_inode_write: Journal has aborted
Feb 15 04:35:59 htpclin kernel: [18086072.740000] __journal_remove_journal_head: freeing b_committed_data
Feb 15 04:35:59 htpclin last message repeated 9 times

```

The box was recording video at the time, there is also a cron job which started at 04:00 and was still running when this happened. The cronjob moves old files from the video partition over the network using cifs to another computer. The cronjob does not move the same files as those that was recorded at the time.

After a reboot when I realized the problem it runned fsck and check the filesystem, reported some errors as FIXED and after this the system seems to work again.

The box runs on a AMD 64 3500+ and is running Ubuntu Dapper with the standard kernel:
"Linux htpclin 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686 GNU/Linux"

The real problem is of course that I would like to know why this happens and if there is a way to fix it. The problem is just that its a bit hard to reproduce it, so my hope is that there is that the logs tells someone what the problem is.

If there isn't a way to fix the problem, is there some way I could get the remount to automatically start a reboot so the system reboots directly runs fsck and startup again when this happens ?

---

