---
title: "grsync throws error after backing up with NO errors!"
date: 2017-11-04
forum: General Help
---

### Post by sterator on 2017-11-04
I'm running 17.04 on a Dual-Xeon Mac Pro. Both boot volume and backup drive are the same model of Samsung SSD, and there is *plenty* of room available on the backup volume to handle the files being backed up, which is what I've designated grsync to back up.

Initial backup: no issues. 2 or 3 subsequent incrementals: no issue.  This morning, tried to do an incremental and got this error:

```
**** Documents > Bento_Backup - Sat Nov  4 15:06:25 2017

** Launching RSYNC command:
rsync -r -t -v --progress -b -s /home/maker/Documents/ /media/maker/Bento_Backup

sending incremental file list
rsync: mkdir "/media/maker/Bento_Backup" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(675) [Receiver=3.1.2]
Rsync process exit status: 11
```

Can anyone help me to interpret this error and how to fix it, please?
Thank you

---

