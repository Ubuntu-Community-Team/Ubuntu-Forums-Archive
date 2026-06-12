---
title: "Backing up data from drive"
date: 2008-03-27
forum: General Help
---

### Post by ElSean on 2008-03-27
I have a mount on my Ubuntu box that I would like to backup to a external USB hard drive.  It's a 200 GB external drive and I only need to back up about 9 GB.  I'm looking to set it up so that it will backup automatically at a specific time each day.  If possible, it would be great to do an incremental backup since 9 GB isn't being changed daily.  Anyone with ideas on how to go about this, advice would be much appreciated.

Thanks!

---

### Post by nick_h on 2008-03-27
Have a look at the *rsync* command:
```
man rsync
```
You could run it as a daily cron job.

---

