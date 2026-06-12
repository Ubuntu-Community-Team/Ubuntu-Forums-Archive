---
title: "Bash script at startup or Cron ?"
date: 2021-09-04
forum: General Help
---

### Post by oygle on 2021-09-04
Trying to free up disk space today and noticed this command

```
#To delete all entries older than two days, use this command:
sudo journalctl --vacuum-time=2d 
```

and it resulted in

> Vacuuming done, freed 1.1G of archived journals from /var/log/journal/....

So, where is the best place for this to be run every day ?  Either a bash script at startup/boot or a cron job ?

---

### Post by norobro on 2021-09-04
You can limit the journal file size by making a change in /etc/systemd/journald.conf (see man 5 journald.conf)

I set the maximum file size on my system to 20 MB by uncommenting "SystemMaxFileSize=" like so:```
$ cat /etc/systemd/journald.conf
...
[Journal]
#Storage=auto
#Compress=yes
#Seal=yes
#SplitMode=uid
#SyncIntervalSec=5m
#RateLimitIntervalSec=30s
#RateLimitBurst=10000
#SystemMaxUse=
#SystemKeepFree=
[COLOR=#ff0000]SystemMaxFileSize=20M[/COLOR]
#SystemMaxFiles=100
...
```Now my logs only take up 48 MB and the log still covers ~6 days:```
$ journalctl --disk-usage
Archived and active journals take up 48.0M in the file system


$ journalctl --no-pager | head -1
-- Journal begins at Mon 2021-08-30 06:51:30 CDT, ends at Sat 2021-09-04 21:45:04 CDT. --

```HTH

---

### Post by oygle on 2021-09-05
Thanks for your reply. I think your approach is better than a bash script or cron job, as it simply takes care of itself. I compared what your specs were with what I have ..There was the obvious difference, this line

```
SystemMaxFileSize=20M
```

plus all these extra lines

> 
#RuntimeMaxUse=
#RuntimeKeepFree=
#RuntimeMaxFileSize=
#RuntimeMaxFiles=100
#MaxRetentionSec=
#MaxFileSec=1month
#ForwardToSyslog=yes
#ForwardToKMsg=no
#ForwardToConsole=no
#ForwardToWall=yes
#TTYPath=/dev/console
#MaxLevelStore=debug
#MaxLevelSyslog=debug
#MaxLevelKMsg=notice
#MaxLevelConsole=info
#MaxLevelWall=emerg
#LineMax=48K
#ReadKMsg=yes


I think if I just left it at filesize 20Mb it would still get very large because there is no time limit, plus it seems I have many errors at present, so the file grows quickly. If I simply set this 

> MaxRetentionSec=2day

then that should be the same as

```
sudo journalctl --vacuum-time=2d
```

---

