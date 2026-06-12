---
title: "Does Clam AV scan for boot sector viruses?"
date: 2006-10-19
forum: General Help
---

### Post by Gotou on 2006-10-19
Hi!  I haven't been able to find a definative answer to whether or not clamscan scans the boot sector for viruses.

I'm getting suspicious about a computer dual booting WinXP and Ubuntu.  Recently I noticed a forced system check error:

"There are differences between boot sector and its backup
Differences (offset : original/backup)"

Then there are several columns of numbers and letters followed by

"Not automatically fixing this"

Googled this and found two references.  One said it was a fat32 problem (my WinXP partition is fat32 to allow access from Ubuntu) and the other suggested unmounting the file system and running fsck.vfat and selecting one of three options:

    1) Copy original to backup
    2) Copy backup to original
    3) No action

I don't want to mess with the boot sector myself if I don't have to.  The differences list seems to be getting longer.  I've run clamscan but I'm not sure if I've added the correct switches/options to the command line.

sudo clamscan -r --stdout --move=/home/gotou/clamav_quarantine/ /home/gotou > clamscan.log

I've got another dual boot computer with Win98 and Ubuntu but it doesn't come with the boot sector differences message.

Any ideas?

Thanks

---

