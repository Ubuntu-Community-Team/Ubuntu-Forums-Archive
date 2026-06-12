---
title: "Cron running PHP script dies with &quot;Could not startup.&quot; error"
date: 2006-08-04
forum: General Help
---

### Post by ifokkema on 2006-08-04
Hi,

I've had my Cron jobs running every day to start my little backup script I have. It used to run fine but now it just doesn't. I can't remember changing anything. The mail I get from Cron just reads:
"Could not startup."
Nothing else. Manually running the script, exactly like in the crontab file, runs perfectly. Googling didn't get me anywhere.

Cron entry:
```
0  22 * * 0   /home/ifokkema/scripts/backup.php backup_00.ini --archives=daily --no-tar
0  22 * * 1-6 /home/ifokkema/scripts/backup.php backup_00.ini
```

File is:
```
-rwxr-xr-x 1 ifokkema ifokkema 22K 2006-06-08 21:09 /home/ifokkema/scripts/backup.php
```

/var/log/syslog shows:
```
Aug  4 22:00:01 localhost /USR/SBIN/CRON[19492]: (ifokkema) CMD (/home/ifokkema/scripts/backup.php backup_00.ini)
```

I have this on **two separate** Dapper installs, which **two different** PHP scripts. Anyone? My guess is that it has to do with PHP running in Cron. Anyone (not) having this problem?

---

### Post by ifokkema on 2006-08-08
OK, just found the problem:
I had been messing around with PHP-GTK and had edited PHP-cli's php.ini to load the gtk.so library. **Apparently, this stops PHP-cli to function completely from cron.** Even a 'Hello world' script didn't run. Have been asking around on the PHP.net lists and someone suggested running php -i (ask for ini information). Since that didn't return anything, I thought about trying php -n (ignore .ini file). Suddenly, it worked...

*SO: Loading the GTK library in your /etc/php4/cli/php.ini, KILLS the PHP-cli functionality from cron.*

---

