---
title: "Cron help (sort of)"
date: 2020-04-10
forum: General Help
---

### Post by Robert_Boutin on 2020-04-10
Sorry for even asking this but I'm having issues with a cron job and I can't figure out why.

I want to run a job every hour of every day at midnight during February, March, and April.  My cronjob is:

0 */1 * 2,3,4 * sh /home/user/scripts/sharerdiff.sh

sharerdiff.sh just backs up a database and data from "Share" to a server named "Backup" using rdiff:

*#!/bin/sh*


*# Database credentials*
*user="user"*
*password="password"*
*db_name="database"*

*# Options*
*date=$(date +"%Y-%m-%d_%H:%M")*

*# Rdiff the data folder*
*sudo su - root -c "rdiff-backup /var/nc_data user@192.168.1.156::/home/user/share/data"*

*# Rdiff the nextcloud folders in /var/www/html/nextcloud*
*sudo su - root -c "rdiff-backup /var/www/html/nextcloud user@192.168.1.156::/home/user/share/webroot"*

*# Dump database into SQL file, rdiff, then remove dumped database*
*sudo su - root -c "mysqldump --single-transaction --user=$user --password=$password nextcloud > /home/user/backup/nextcloud_$date.sql"*
*sudo su - root -c "rsync -avz /home/user/backup/nextcloud_$date.sql user@192.168.1.156:/home/user/share/database/"*
*sudo su - root -c "rm /home/user/backup/*"*

*# Remove old backups*
*sudo su - root -c "rdiff-backup --remove-older-than 7Y user@192.168.1.156::/home/user/share/data"*
*sudo su - root -c "rdiff-backup --remove-older-than 1Y user@192.168.1.156::/home/user/share/webroot"*


My problem is that every day, it doesn't back up at 04:00 or 05:00 and I can't figure out what might be preventing it from backing up.  The contents of 3 days of rdiff-backup-data on Backup is below, you can see the missing backups at the same times each day.  Any thoughts as to why that might be happening?  Suggestions of where to look?  Thanks as always.

[TABLE="width: 1500"]
[TR]
[TD]*-rw-------   1 user user     492 Apr  7 00:00 session_statistics.2020-04-07T00:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 01:00 session_statistics.2020-04-07T01:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 02:00 session_statistics.2020-04-07T02:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 03:00 session_statistics.2020-04-07**[COLOR=#ff0000]T03:00:02[/COLOR]**-04:00.data*
*-rw-------   1 user user     492 Apr  7 06:00 session_statistics.2020-04-07**[COLOR=#ff0000]T06:00:02[/COLOR]**-04:00.data*
*-rw-------   1 user user     492 Apr  7 07:00 session_statistics.2020-04-07T07:00:03-04:00.data*
*-rw-------   1 user user     492 Apr  7 08:00 session_statistics.2020-04-07T08:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 09:00 session_statistics.2020-04-07T09:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 10:00 session_statistics.2020-04-07T10:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 11:00 session_statistics.2020-04-07T11:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 12:00 session_statistics.2020-04-07T12:00:02-04:00.data*
*-rw-------   1 user user     520 Apr  7 13:00 session_statistics.2020-04-07T13:00:02-04:00.data*
*-rw-------   1 user user     519 Apr  7 14:00 session_statistics.2020-04-07T14:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 15:00 session_statistics.2020-04-07T15:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  7 16:00 session_statistics.2020-04-07T16:00:02-04:00.data*
*-rw-------   1 user user     512 Apr  7 17:00 session_statistics.2020-04-07T17:00:02-04:00.data*
*-rw-------   1 user user     521 Apr  7 18:00 session_statistics.2020-04-07T18:00:02-04:00.data*
*-rw-------   1 user user     521 Apr  7 19:00 session_statistics.2020-04-07T19:00:01-04:00.data*
*-rw-------   1 user user     525 Apr  7 20:00 session_statistics.2020-04-07T20:00:02-04:00.data*
*-rw-------   1 user user     513 Apr  7 21:00 session_statistics.2020-04-07T21:00:02-04:00.data*
*-rw-------   1 user user     523 Apr  7 22:00 session_statistics.2020-04-07T22:00:02-04:00.data*
*-rw-------   1 user user     536 Apr  7 23:00 session_statistics.2020-04-07T23:00:02-04:00.data*
*-rw-------   1 user user     534 Apr  8 00:00 session_statistics.2020-04-08T00:00:02-04:00.data*
*-rw-------   1 user user     517 Apr  8 01:00 session_statistics.2020-04-08T01:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  8 02:00 session_statistics.2020-04-08T02:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  8 03:00 session_statistics.2020-04-08**[COLOR=#ff0000]T03:00:02[/COLOR]**-04:00.data*
*-rw-------   1 user user     492 Apr  8 06:00 session_statistics.2020-04-08**[COLOR=#ff0000]T06:00:02[/COLOR]**-04:00.data*
*-rw-------   1 user user     492 Apr  8 07:00 session_statistics.2020-04-08T07:00:03-04:00.data*
*-rw-------   1 user user     492 Apr  8 08:00 session_statistics.2020-04-08T08:00:02-04:00.data*
*-rw-------   1 user user     520 Apr  8 09:00 session_statistics.2020-04-08T09:00:02-04:00.data*
*-rw-------   1 user user     513 Apr  8 10:00 session_statistics.2020-04-08T10:00:02-04:00.data*
*-rw-------   1 user user     525 Apr  8 11:00 session_statistics.2020-04-08T11:00:02-04:00.data*
*-rw-------   1 user user     517 Apr  8 12:00 session_statistics.2020-04-08T12:00:02-04:00.data*
*-rw-------   1 user user     520 Apr  8 13:00 session_statistics.2020-04-08T13:00:02-04:00.data*
*-rw-------   1 user user     532 Apr  8 14:00 session_statistics.2020-04-08T14:00:02-04:00.data*
*-rw-------   1 user user     518 Apr  8 15:00 session_statistics.2020-04-08T15:00:01-04:00.data*
*-rw-------   1 user user     527 Apr  8 16:00 session_statistics.2020-04-08T16:00:02-04:00.data*
*-rw-------   1 user user     524 Apr  8 17:00 session_statistics.2020-04-08T17:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  8 18:00 session_statistics.2020-04-08T18:00:02-04:00.data*
*-rw-------   1 user user     523 Apr  8 19:00 session_statistics.2020-04-08T19:00:02-04:00.data*
*-rw-------   1 user user     523 Apr  8 20:00 session_statistics.2020-04-08T20:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  8 21:00 session_statistics.2020-04-08T21:00:01-04:00.data*
*-rw-------   1 user user     538 Apr  8 22:00 session_statistics.2020-04-08T22:00:01-04:00.data*
*-rw-------   1 user user     517 Apr  8 23:00 session_statistics.2020-04-08T23:00:02-04:00.data*
*-rw-------   1 user user     534 Apr  9 00:00 session_statistics.2020-04-09T00:00:02-04:00.data*
*-rw-------   1 user user     517 Apr  9 01:00 session_statistics.2020-04-09T01:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  9 02:00 session_statistics.2020-04-09T02:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  9 03:00 session_statistics.2020-04-09**[COLOR=#ff0000]T03:00:03[/COLOR]**-04:00.data*
*-rw-------   1 user user     492 Apr  9 06:00 session_statistics.2020-04-09**[COLOR=#ff0000]T06:00:03[/COLOR]**-04:00.data*
*-rw-------   1 user user     511 Apr  9 07:00 session_statistics.2020-04-09T07:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  9 08:00 session_statistics.2020-04-09T08:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  9 09:00 session_statistics.2020-04-09T09:00:02-04:00.data*
*-rw-------   1 user user     522 Apr  9 10:00 session_statistics.2020-04-09T10:00:02-04:00.data*
*-rw-------   1 user user     520 Apr  9 11:00 session_statistics.2020-04-09T11:00:02-04:00.data*
*-rw-------   1 user user     520 Apr  9 12:00 session_statistics.2020-04-09T12:00:02-04:00.data*
*-rw-------   1 user user     514 Apr  9 13:00 session_statistics.2020-04-09T13:00:02-04:00.data*
*-rw-------   1 user user     492 Apr  9 14:00 session_statistics.2020-04-09T14:00:02-04:00.data*
[/TD]
[/TR]
[/TABLE]

---

### Post by lvm on 2020-04-11
crontab line looks ok (except for excessive sh and /1 in hours but it shouldn't be an issue). When cron runs a command it logs it to /var/log/syslog and that's were one should look to see whether it works as expected. If it is there, something's wrong in the script. Or maybe not wrong, just no changes at that time. Logging would've helped, it is always a good idea to add as much logging as possible.

---

### Post by Robert_Boutin on 2020-04-11
Thanks.  /var/log/syslog shows that cron executed my script on the hour including the two hours that didn't back up:

Apr 11 04:00:01 share CRON[18657]: (root) CMD (sh /home/user/scripts/sharerdiff.sh)
Apr 11 05:00:01 share CRON[20795]: (root) CMD (sh /home/user/scripts/sharerdiff.sh)

If I read your comment correctly, you are saying if there are no changes to the data, then rdiff-backup won't log an event (don't know if I said that correctly)?  I understand rdiff-backup does differential backups and that if there is no data change, there is no differential data to back up.  But I would have thought there would still be an event logged at 04:00 and 05:00 even if the data didn't change from 03:00.  Maybe not, you obviously could tell this is not my forte.  I'll have to dig into the rdiff-backup man page, maybe it's as simple as what you say.

---

### Post by norobro on 2020-04-11
> **Robert_Boutin said:**
> ... But I would have thought there would still be an event logged at 04:00 and 05:00 even if the data didn't change from 03:00. ...As a test I ran rdiff-backup twice in a row on a directory with no changes in between and a "*.data" file was generated for both sessions.```
[SIZE=2][COLOR=#5454FF][FONT=monospace]**~/bar/rdiff-backup-data**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ ls -lGg session*  [/FONT][/COLOR]
[/SIZE][FONT=monospace][SIZE=2]-rw------- 1 462 Apr 11 18:19 session_statistics.2020-04-11T18:19:53-05:00.data
-rw------- 1 462 Apr 11 18:19 session_statistics.2020-04-11T18:19:57-05:00.data[/SIZE]
[/FONT]
```Perhaps bumping the the verbosity level up will give you a clue as to what is happening. ```
rdiff-backup -v9 ...
```

---

### Post by lvm on 2020-04-12
I have no experience with rdiff, but I would've added  '>> /var/log/backup.log' to cron line to save all the output of the script to see what's going on and maybe some extra info lines to the script.

---

