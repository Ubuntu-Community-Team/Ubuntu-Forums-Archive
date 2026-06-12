---
title: "Backup in external hard disk through grsync"
date: 2023-11-29
forum: General Help
---

### Post by AnupamMitra on 2023-11-29
My OS in PC is UBUNTU 22.04.  I'm using Grsync since long. But today during creating backup when I pressed the big blue i button it shows the following error message.
```

rsync: [generator] recv_generator: failed to stat "/media/anupam/ubuntu/anupam/.audacity-data/audacity.cfg": Bad message (74)
rsync: [generator] recv_generator: failed to stat "/media/anupam/ubuntu/anupam/.cache/gnome-calculator/eurofxref-daily.xml": Bad message (74)
rsync: [generator] recv_generator: failed to stat "/media/anupam/ubuntu/anupam/.cache/gnome-desktop-thumbnailer/gstreamer-1.0/gstreamer-1.0.registry": Structure needs cleaning (117)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1338) [sender=3.2.7]
Rsync process exit status: 23

```
Further, synchronisation is also not done perfectly. Need suggestion to resolve the issue.

---

### Post by TheFu on 2023-11-29
Do you really want to backup cache files?  They aren't useful in backups, so most people would exclude those.

BTW, rsync is great for mirroring stuff, but not the best option for backups.  Backups should be versioned and take just a few seconds to complete after the initial backup.  I love the way a mirror copy can be restored easily. Some backup tools retain the most recent backup as a mirror, with older verions as diffs off that mirror.  The best of both worlds.

If your backup only includes your HOME directory, then rdiff-backup can be used to achieve both the mirror and versions in a fairly efficient (storage AND time).

I couldn't find what "bad message" 74 meant.  My first guess would be a corrupted file system - either the source or the target, so I'd run **fsck** against both, assuming native Linux file systems are used (which is required for backups).  While I was at it, I'd run SMART tests against both storage devices too.

---

### Post by AnupamMitra on 2023-12-08
> **TheFu said:**
> Do you really want to backup cache files?  They aren't useful in backups, so most people would exclude those.

BTW, rsync is great for mirroring stuff, but not the best option for backups.  Backups should be versioned and take just a few seconds to complete after the initial backup.  I love the way a mirror copy can be restored easily. Some backup tools retain the most recent backup as a mirror, with older verions as diffs off that mirror.  The best of both worlds.

If your backup only includes your HOME directory, then rdiff-backup can be used to achieve both the mirror and versions in a fairly efficient (storage AND time).

I couldn't find what "bad message" 74 meant.  My first guess would be a corrupted file system - either the source or the target, so I'd run **fsck** against both, assuming native Linux file systems are used (which is required for backups).  While I was at it, I'd run SMART tests against both storage devices too.

 Thanks for your reply. I couldn't reply in time on account of my indisposition. 

No, I do not want to backup cache files. However, in your opinion which is/are the best backup tool/s?

---

### Post by TheFu on 2023-12-08
> **AnupamMitra said:**
> No, I do not want to backup cache files. However, in your opinion which is/are the best backup tool/s?

That depends on many things.  The backup tool you will actually use is the best, but it should have some characteristics.

The Checklist

[LIST]
[*]    Stable / Works Every Time
[*]    Automatic
[*]    Different Storage Media
[*]    Fast
[*]    Efficient
[*]    Secure
[*]    Versioned
[*]    Offsite / Remote
[*]    Restore Tested
[/LIST]
Ref: [https://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](https://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups) lays out 9 items to look for in a backup tool/solution.  The link explains each. I'd add 1 more - you will use it. Editing that blog entry is too hard now, but that would round out to "10".  People like lists of 10.

If you just need to backup specific files, not the entire system, there are lots of choices.  This avoids the entire backup of boot files and restoring those files exactly where needed issue.  My backups don't deal with boot files because my restore process always starts with a fresh, minimal, OS, install, before I restore anything else.  This method provides lots of flexibility, but there is 1 downside.  My backups will not reproduce a 100% same system after restore.  If that is required, expect to waste lots of extra time and storage doing backups.  But if having a system that 100% feels the same as before is sufficient, with the settings and data that was there before, even if some program versions are slightly different, then my method vastly reduces the storage required and the time for backups.

I've posted at least 50 times how I backup my systems and perhaps 5 times how I restore things.  You've been here long enough to search to find those posts.


And for the record, the backup tool that I use is **rdiff-backup**.  That's the best tool for my needs. Anyone using rsync for backups really should look at it, since the options on the command line are very, very, similar to what rsync uses. Basically, using rdiff-backup in stead of rsync gains most of the things in my _Top 10_ list above.  BTW, rdiff-backup is actually faster than rsync for all but the very first backup run.

---

### Post by AnupamMitra on 2023-12-08
> **TheFu said:**
> That depends on many things.  The backup tool you will actually use is the best, but it should have some characteristics.

The Checklist

[LIST]
[*]    Stable / Works Every Time 
[*]    Automatic 
[*]    Different Storage Media 
[*]    Fast 
[*]    Efficient 
[*]    Secure 
[*]    Versioned 
[*]    Offsite / Remote 
[*]    Restore Tested 
[/LIST]
Ref: [https://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](https://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups) lays out 9 items to look for in a backup tool/solution.  The link explains each. I'd add 1 more - you will use it. Editing that blog entry is too hard now, but that would round out to "10".  People like lists of 10.

If you just need to backup specific files, not the entire system, there are lots of choices.  This avoids the entire backup of boot files and restoring those files exactly where needed issue.  My backups don't deal with boot files because my restore process always starts with a fresh, minimal, OS, install, before I restore anything else.  This method provides lots of flexibility, but there is 1 downside.  My backups will not reproduce a 100% same system after restore.  If that is required, expect to waste lots of extra time and storage doing backups.  But if having a system that 100% feels the same as before is sufficient, with the settings and data that was there before, even if some program versions are slightly different, then my method vastly reduces the storage required and the time for backups.

I've posted at least 50 times how I backup my systems and perhaps 5 times how I restore things.  You've been here long enough to search to find those posts.


And for the record, the backup tool that I use is **rdiff-backup**.  That's the best tool for my needs. Anyone using rsync for backups really should look at it, since the options on the command line are very, very, similar to what rsync uses. Basically, using rdiff-backup in stead of rsync gains most of the things in my _Top 10_ list above.  BTW, rdiff-backup is actually faster than rsync for all but the very first backup run.

Thanks for detailed guidance. However, please advise which method I should adopt to install rdiff-backup on my Ubuntu 22.04 - apt-get, apt or aptitude. 

However, the size of my external HDD is 2 TB with two partitions - one for Windows (allotted space is 428 GB) and the other for Ubuntu.  This time I would prefer to backup all my files other than the entire system/boot files.

---

