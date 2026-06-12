---
title: "Backup program suggestions"
date: 2013-02-08
forum: General Help
---

### Post by AlphaLupi on 2013-02-08
I've tried several of the backup solutions available on Synaptic, but none have been a good fit for me.

I'd like to find a program that can:

1. Run at a scheduled time
2. Run multiple backup profiles
3. Compress the backed-up files
4. Save to an external drive, and possible to an FTP site as well.
5. Can run in the background.

Does anyone have any suggestions?

---

### Post by landersohn on 2013-02-08
I am using sbackup
- runs in background
- compression is an option
- saves to any drive, so external hdd is not a problem, don't think I can do ftp though. Do you really want to send your stuff through an unsecure connection?
- you can schedule with cron to do night backups, it may have this option in the GUI
- it has a command line option for the config file to use which should give you support for multiple profiles

---

### Post by Mopar1973Man on 2013-02-08
I'm using Grsync and backing up a 1.0 TB drive to a 1.5 TB drive. I've a built a script to execute on my own time. Being that my PC typically goes asleep after 30 minutes (conserving power). So if I'm going to be working with the computer for a good part of the day I'll fire the backup script.

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

### Post by Habitual on 2013-02-08
```
rsync +.tar.gz
```

or [http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/) for the scripting-impaired. :)

---

### Post by LewisTM on 2013-02-08
I use Luckybackup. It can set up a series of rsync tasks, log the results and schedule backups to run via cron, in the background.

For compression, I backup to a btrfs partition with LZO compression turned on.

Cheers!

---

### Post by landersohn on 2013-02-08
Another thought comes to mind: do you need to backup an sql database?
backupninja lets you write scripts and call mysqldump automatically as part of the backup process

---

