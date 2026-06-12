---
title: "Bash script - something isn't quite right."
date: 2016-10-22
forum: General Help
---

### Post by Roasted on 2016-10-22
Hi friends. I put together a bash script in an effort to make my off-site-backup easier. My off-site plan is to simply keep an external hard drive in my desk at work. I work close to home, so coming home for lunch is frequent. Once a week, bring the drive with, plug in to my server, run the script, take it back when lunch is over. That way my most important stuff can be retrieved without worrying about some sort of cloud service.

Here's the script:

```

#!/bin/bash
mount /dev/disk/by-uuid/06112c0c-e245-4be8-a03a-d861b6890374 /media/off-site-drive/
if findmnt UUID=0611280c-eb45-4be8-a02a-d861b6890374 > /dev/null; then
echo Backup drive mounted. Backup starting...
else
echo Backup drive not found.
fi
errval=$?
rsync -a --delete /media/vault/backups /media/off-site-drive/
echo Backups directory complete
rsync -a --delete /media/vault/documents /media/off-site-drive/
echo Documents directory complete
rsync -a --delete /media/vault/music /media/off-site-drive/
echo Music directory complete
rsync -a --delete /media/vault/pictures /media/off-site-drive/
echo Pictures directory complete
umount /media/off-site-drive
echo The backup drive has been ejected
if [[ "$errval" == "0" ]]; then
echo ----Backup Complete: Backups, Documents, Music, Pictures----
else
echo ERROR: BACKUP FAILED
fi
exit

```

The goals:
1) When the script is launched, have it mount the backup drive.
2) Have the script tell if the backup drive is mounted, and fail the job if the backup drive is not found *OR* if an rsync error occurs.
3) Have "backup complete" and "backup failed" echo alerts.

What happens:
The backup drive is currently maxed. I took this opportunity to make sure it alerts me on the inevitable rsync failure. It didn't, but instead still spits out the output "Backup Complete: etc etc"

So basically, what I have here functions, it just doesn't handle the error notification as I had hoped. Where did I goof?

---

### Post by TheFu on 2016-10-22
You need to check $? immediately after each call. Do not call "echo" first.
The line where you copy $? into retval only works once. It isn't a pointer, it is a copy from that instant, not constantly updated.

#!/bin/bash  -x

should help.  [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) has more best practices.

---

