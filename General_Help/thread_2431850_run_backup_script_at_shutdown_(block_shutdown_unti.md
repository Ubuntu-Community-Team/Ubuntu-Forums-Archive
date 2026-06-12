---
title: "run backup script at shutdown (block shutdown until down)"
date: 2019-11-22
forum: General Help
---

### Post by bjlockie on 2019-11-22
I'm trying to run a back backup script at shutdown but I want shutdown to wait until the script is done.
It was suggested I could try appending my script to /usr/share/sddm/scripts/Xstop.
Shutdown seems to keep happening or maybe something kills my script for taking too long.

> 
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(644) [sender=3.1.3]
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at io.c(513) [generator=3.1.3]


---

### Post by TheFu on 2019-11-23
Why not just add a shutdown to the end of the backup script?
Both run as root, right?

Here's my root crontab on a laptop:
```
1  0  * * * /root/bin/back-suspend.sh 
```

Here's that script:
$ more ~/bin/back-suspend.sh 
```
#!/bin/bash

/root/bin/backup-to-rom.sh 
/usr/sbin/pm-suspend
```
The suspend could easily be  ** /sbin/shutdown now**

I only suspend this specific machine. If the backups are "pulled" from the backup server to mitigate malware attacks, then the first command would likely be named "pull-backup-on-posc.sh" and **ssh root@posc /sbin/shutdown now** would be the 2nd, assuming remote root from the backup server via ssh has been allowed.

---

