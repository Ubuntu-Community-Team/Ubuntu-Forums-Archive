---
title: "Use Rsync to backup Windows 10 partition"
date: 2020-03-29
forum: General Help
---

### Post by ping-wu on 2020-03-29
Has anyone ever successfully backed up and restored Windows partition in Ubuntu?

---

### Post by TheFu on 2020-03-30
Only data, never the OS w/ rsync.

i have used linux storage for Windows backups using fsarchiver and ddrescue, but those were created using a small Linux flash-boot setup.  About 10 yrs ago, i stopped leaving data on Windows disks at all and directly store all that data onto Samba shares backed by Linux-controlled storage.  Made my life 1000x easier and, for me, much safer since i know exactly how to backup linux storage, perfectly, 100%.

About 10 yrs ago, as a replacement HDD was being swapped into a Windows laptop to expand storage, i tried to get the Win7 built-in backup tool to work.  it never did.  The resulting system wouldn't boot.  Using unix tools to compare both the old and the new data showed they were not identical. Did a little research online and saw a Windows Backup Tools Comparison (from a reputable tech site/reviewers whose names we all know) where they were comparing the source and backup data.  Out of 10 tools, only 1 - ONE! - created an identical restore when compared.  These were mostly famous, well-advertised, branded, commercial Windows backup tools.  The built-in backup for the OS failed them too.

---

### Post by kneutron on 2020-04-07
--If you want a good reliable bare-metal OS backup and restore for Win, try veeam or AOMEI. Don't try it from the Linux side unless (as mentioned above) it's for data files only, because especially with UEFI it probably won't be able to boot when you try restoring it.

[https://www.veeam.com/virtual-machine-backup-solution-free.html](https://www.veeam.com/virtual-machine-backup-solution-free.html)

[https://www.aomeitech.com/aomei-backupper.html](https://www.aomeitech.com/aomei-backupper.html)

---

