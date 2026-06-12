---
title: "Rsnapshot hangs on ' setting locale to posix c '"
date: 2013-01-07
forum: General Help
---

### Post by chopstickkk on 2013-01-07
I'm getting started with rsnapshot but it seems to hang for 2-3 minutes on when setting the locale, or perhaps just after. It's a shame because the rest of the process is lightening fast.

Any clues would be greatly appreciated as always!

Thanks in advance,
John.

Here's the log of 3 snapshots...

```
[07/Jan/2013:10:46:57] require Lchown
[07/Jan/2013:10:46:57] Lchown module not found
[07/Jan/2013:10:46:57] /usr/local/bin/rsnapshot onboot: started
[07/Jan/2013:10:46:57] Setting locale to POSIX "C"
[07/Jan/2013:10:49:44] mkdir -m 0755 -p /media/backup-2012-11-20/backup-rsnapshot/onboot.0/
[07/Jan/2013:10:49:44] /usr/bin/rsync -avvv --delete --numeric-ids --relative --delete-excluded /usr/local/bin /media/backup-2012-11-20/backup-rsnapshot/onboot.0/
[07/Jan/2013:10:49:45] touch /media/backup-2012-11-20/backup-rsnapshot/onboot.0/
[07/Jan/2013:10:49:45] /usr/bin/logger -i -p user.info -t rsnapshot /usr/local/bin/rsnapshot onboot: completed successfully
[07/Jan/2013:10:49:45] /usr/local/bin/rsnapshot onboot: completed successfully
[07/Jan/2013:10:53:18] require Lchown
[07/Jan/2013:10:53:18] Lchown module loaded successfully
[07/Jan/2013:10:53:18] /usr/local/bin/rsnapshot onboot: started
[07/Jan/2013:10:53:18] Setting locale to POSIX "C"
[07/Jan/2013:10:55:14] /bin/cp -al /media/backup-2012-11-20/backup-rsnapshot/onboot.0 /media/backup-2012-11-20/backup-rsnapshot/onboot.1
[07/Jan/2013:10:55:14] /usr/bin/rsync -avvv --delete --numeric-ids --relative --delete-excluded /usr/local/bin /media/backup-2012-11-20/backup-rsnapshot/onboot.0/
[07/Jan/2013:10:55:14] touch /media/backup-2012-11-20/backup-rsnapshot/onboot.0/
[07/Jan/2013:10:55:14] /usr/bin/logger -i -p user.info -t rsnapshot /usr/local/bin/rsnapshot onboot: completed successfully
[07/Jan/2013:10:55:14] /usr/local/bin/rsnapshot onboot: completed successfully
[07/Jan/2013:10:59:50] require Lchown
[07/Jan/2013:10:59:50] Lchown module loaded successfully
[07/Jan/2013:10:59:50] /usr/local/bin/rsnapshot onboot: started
[07/Jan/2013:10:59:50] Setting locale to POSIX "C"
[07/Jan/2013:11:02:00] mv /media/backup-2012-11-20/backup-rsnapshot/onboot.1/ /media/backup-2012-11-20/backup-rsnapshot/onboot.2/
[07/Jan/2013:11:02:00] /bin/cp -al /media/backup-2012-11-20/backup-rsnapshot/onboot.0 /media/backup-2012-11-20/backup-rsnapshot/onboot.1
[07/Jan/2013:11:02:05] /usr/bin/rsync -avvv --delete --numeric-ids --relative --delete-excluded /usr/local/bin /media/backup-2012-11-20/backup-rsnapshot/onboot.0/
[07/Jan/2013:11:02:05] touch /media/backup-2012-11-20/backup-rsnapshot/onboot.0/
[07/Jan/2013:11:02:05] /usr/bin/logger -i -p user.info -t rsnapshot /usr/local/bin/rsnapshot onboot: completed successfully
[07/Jan/2013:11:02:05] /usr/local/bin/rsnapshot onboot: completed successfully
```

---

