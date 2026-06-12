---
title: "rdiff-backup error"
date: 2020-05-07
forum: General Help
---

### Post by Quarkrad on 2020-05-07
Running 20.04.  I've written a systemd service unit script that runs a script just before Shutdown.  The script runs a test rdiff-backup up command backing up my Documents folder to a local backup HD installed in my pc.  Sometimes it works sometimes it doesn't - specifically I add text to a file and it is not always updated.  If I change the script to a rsync command it works every time.  The scripts are:

service unit  /lib/systemd/system

```
Unit]
Description=Run my custom task at shutdown
DefaultDependancies=no
Before=shutdown.target
After=final.target

[Service]
Type=oneshot
ExecStart=/bin/true
ExecStop=/usr/bin/backup.sh
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target

```

rdiff-backup script /usr/bin/backup.sh

```

#!/bin/bash

 sudo rdiff-backup  /home/dad/Documents /media/dad/backup/rdiffbackup/Documents

```

When I shutdown I hear my mechanical backup disk being written to, and during my testing the time varies, so it appears the backup.service file is working and not shutting down before the backup script finishes.  The log files of the service.backup file show that it always successfully runs. 

```
dad@dadubuntu:~$ systemctl status backup.service
&#9679; backup.service - Run my custom task at shutdown
     Loaded: loaded (/lib/systemd/system/backup.service; enabled; vendor preset>
     Active: active (exited) since Thu 2020-05-07 09:21:11 BST; 20min ago
    Process: 995 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 995 (code=exited, status=0/SUCCESS)

May 07 09:21:11 dadubuntu systemd[1]: Starting Run my custom task at shutdown...
May 07 09:21:11 dadubuntu systemd[1]: Finished Run my custom task at shutdown.
lines 1-8/8 (END)

```

At this point (having rebooted) and the rdiff-backup script not having updated my test file I decided to run the rdiff-backup scirpt manually to see if there was a problem with it working in conjunction with the service unit file. I got the following message

```
dad@dadubuntu:~$ sh '/usr/bin/backup.sh' 
Fatal Error: It appears that a previous rdiff-backup session with process
id 2172 is still running.  If two different rdiff-backup processes write
the same repository simultaneously, data corruption will probably
result.  To proceed with regress anyway, rerun rdiff-backup with the
--force option.

```

This should not be happening as the rdiff-backup process was run at shutdown and now sometime having rebooted (10 minutes). Any advice what I do from here would be most appreciated.

---

### Post by slickymaster on 2020-05-07
*Thread moved to **General Help**.*

---

### Post by TheFu on 2020-05-07
No answer from me. Sorry.

20.04 changed from python2 to python3 for rdiff-backup.  That's a good thing to keep the project alive.  It also broke compatibility between different versions of rdiff-backup. The clients and servers must run the exact same version, it seems.  I ran into that in the 12.04 --> 14.04 timeframe.  16.04 retained the same version.  

There have been debates whether the backup directory files are or are not compatible. The core devs seem to think they are.  I haven't been able to use rdiff-backup on my 20.04 systems (a server and a desktop) because my backup server runs an older version. Haven't decided what I'll do for backups on 20.04 systems yet, since changing the 16.04 backup server will break backups for about 20 other systems.

I wouldn't let systemd control this for a number of reasons.  systemd has a built-in timeout for all processes, unless you override it in the Unit file or set it to be infinite.  At some point, for some reason, I bet a backup job will fail to complete before the backup finishes, probably due to the default timeout.  The first time that happens, at the next run, rdiff-backup has to waste a few minutes reverting.  That adds 2 minutes, perhaps 30 minutes to the job.  It won't get better.  Using cron to backup then go into standby nightly has been my solution for 1 box.  I can run it earlier, but it runs automatically at 00:07 am.

When rdiff-backup jobs corrupt the backup area, a different message is displayed.  Whenever that has happened to me, I move the old backup area to a different directory, create a fresh directory for all new backups to be placed, then set an **at** job to be run in 30 days that wipes the moved directory.  And I forget about the issue as new daily backups work.  In about 10 yrs of using rdiff-backup, that sort of corruption has happened 3 times total across a number of daily backups for a number of machines.  Just 3 times and always on systems where I wasn't using LVM snapshots to quiesce the backup files completely.

I'd move the directory and manually run the backups, then change the backups not to use systemd for management.

---

