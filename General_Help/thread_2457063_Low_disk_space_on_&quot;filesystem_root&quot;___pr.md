---
title: "Low disk space on &quot;filesystem root&quot;   problem"
date: 2021-01-25
forum: General Help
---

### Post by ra7411 on 2021-01-25
Low disk space on "filesystem root"
The volume filesystem root has only 0 bytes disk space remaining.

Out of nowhere, I've started getting messages about disk space problems.
This 18.04 install has been working fine, this recent message showed up while running Grsync backup.
The disk is a samsung ssd 500g, which is normally 45 pct filled, right now Disks show it 100 pct filled. SDA1 os is 31 gbs.

How do I fix this?

---

### Post by ra7411 on 2021-01-25
Here's terminal output of df -h   and df -hi /    ,  if that helps.

---

### Post by Impavidus on 2021-01-25
Try to find the files taking all that space. As this happend while running backups, make sure the backup partition was actually mounted. If it wasn't, the files have been copied to some place on your root file system. I'd first look in the directory that you use as mountpoint for your backup drive.

---

### Post by VMC on 2021-01-25
Find out where your large usage is:
```
sudo find / -type f -exec du -h {} + | sort -hr | head -20
```

---

### Post by ra7411 on 2021-01-25
> **Impavidus said:**
> Try to find the files taking all that space. As this happend while running backups, make sure the backup partition was actually mounted. If it wasn't, the files have been copied to some place on your root file system. I'd first look in the directory that you use as mountpoint for your backup drive.


I think you got it, the Grsync destination was unmounted. Very weird, I've been doing this backup daily for several years with no problems like this, I would have guessed Grsync had a way of making sure the destination was mounted or it would abort.

So far that looks like the fix for the problem.  I'll wait a couple days before going "solved" on this.

Thanks

---

