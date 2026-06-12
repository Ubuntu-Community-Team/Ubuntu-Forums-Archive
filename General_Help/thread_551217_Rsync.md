---
title: "Rsync"
date: 2007-09-14
forum: General Help
---

### Post by hebetude on 2007-09-14
I've heard of it, but it seems very daunting to setup.  Here's what I want to do backup my apps folder to a backup folder on a different hdd (same computer).  I'd like to do a full backup every month and an incremental once a week.  

This is a combination of things I've read (untested!).  Let me know if this is done wrong.  I'm going to implement it on my system and see how it works.

Thanks for any help,


This puts a cron job to make a full backup to /mnt/music/backup/apps once a month.
```
crontab -e 
0 0 1 * * rsync -a --delete /mnt/xtra/apps /mnt/music/backup >/dev/null
```

This is going to setup a 4week incremental backup.  Add this to your weekly crontab
0 0 * * 1             /usr/local/bin/weekly_snapshot.sh >/dev/null

The first one will run at midnight on the first day of the month, the second runs every monday.  The >/dev/null keeps crontab from reporting every single thing it does to your mail, this way it will only report stderr to your mail (errors).

[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync]("http://www.mikerubel.org/computers/rsync_snapshots/#Rsync")
> Update (2003.05.02): John Pelan writes in to suggest recycling the oldest snapshot instead of recursively removing and then re-creating it. This should make the process go faster, especially if your file tree is very large:

```
#!/bin/sh
# directory to backup
BDIR=/mnt/xtra/apps

# backup directory
WDIR=/mnt/music/backup

mv $WDIR/backup.3 $WDIR/backup.tmp
mv $WDIR/backup.2 $WDIR/backup.3
mv $WDIR/backup.1 $WDIR/backup.2
mv $WDIR/backup.0 $WDIR/backup.1
mv $WDIR/backup.tmp $WDIR/backup.0
cp -al $WDIR/backup.1/. $WDIR/backup.0
rsync -a --delete $BDIR/ $WDIR/backup.0/

```
backup.0 is the newest, backup.3 is the oldest.
It's scary to me to try such untested things, but it's all copies outside of the backup folders so giving I'm just giving it a whirl so to speak

---

### Post by psusi on 2007-09-14
I don't have the code in front of me but I wrote a little shell script to run things like this from cron, but instead of dumping the output to null, it writes stdout and stderr to a tmp file, then if the command returns an error, cats the tmp file, and finally deletes the tmp file.  This way cron emails you the full output if something went wrong, not just stderr.

---

### Post by akniss on 2007-09-14
```
sudo apt-get install sbackup
```

---

### Post by hebetude on 2007-09-15
> **akniss said:**
> ```
sudo apt-get install sbackup
```

n00b friendly, I like it!

sudo apt-get install sbackup
```

0 upgraded, 108 newly installed, 0 to remove and 0 not upgraded.
Need to get 7553kB/7936kB of archives.
After unpacking 47.8MB of additional disk space will be used.

``` 
Jeebus

---

### Post by akniss on 2007-09-16
It might be installed by default in Feisty.  Either go to System > Administration > Simple Backup Config *OR* hit Alt + F2 and type ```
gksudo simple-backup-config
```

---

