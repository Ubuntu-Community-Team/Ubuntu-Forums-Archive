---
title: "Nightly Backup?"
date: 2007-02-16
forum: General Help
---

### Post by JamesH106 on 2007-02-16
Hey there!

I've just set up a mail server for work. It has:

hda: 40GB Hard Drive
hdb: 100MB Zip Drive
hdc: 40GB Hard Drive

..and runs Ubuntu 6.10 Server Edition

I would like to be able to backup everything on hda to hdc every night, so that in case of hard drive falier I will have a backup. How do I go about doing this?

Also, is it adviseable to backup /boot onto the 100MB?


Thanks a lot!
James.

---

### Post by charl.ie on 2007-02-16
Do you need to back up the whole system, or just parts of it (like just the mail)?

```
rsync -aq /directory/of/mail /mount/point/of/hdc
```
Set that to run with cron every night. Edit /etc/crontab:
```
sudo gedit /etc/crontab
```
and add the line:
0 21 * * * root rsync -aq /directory/of/mail /mount/point/of/hdc

This means that /directory/of/mail will be copied to /monut/point/of/hdc at 9:00pm every night

---

### Post by JamesH106 on 2007-02-16
That's great, but can I make it so that it overwrites existing files?

---

### Post by MatthewMetzger on 2007-02-17
> **JamesH106 said:**
> That's great, but can I make it so that it overwrites existing files?

I'm not an expert in backup, but I do have to keep backups of important user accounts and internal databases for our organization.

I'd recommend that you not overwrite the previous backup data each night. The reason for this is that something could go wrong on Friday and you wouldn't catch it until Monday and the backup with the correct data would be gone because it was overwritten on Friday night.

I create versioned backups, a snapshot of the day and keep a copy of each one. Yes, it does take up a lot of disk space and it probably could be done better than I do it, but it has been very helpful in a couple of cases where people deleted something they needed and didn't realize it until a month later.

I have a script that creates an archive with the day's date as its name.

-Matthew

---

### Post by charl.ie on 2007-02-17
add the --delete option and it will delete any files that have been deleted since the last backup. Rsync is clever enough to know wether it should overwrite the file or not, so you don't have to transfer everything over again.

---

### Post by Falcorian on 2007-02-18
> **MatthewMetzger said:**
> I'm not an expert in backup, but I do have to keep backups of important user accounts and internal databases for our organization.

I'd recommend that you not overwrite the previous backup data each night. The reason for this is that something could go wrong on Friday and you wouldn't catch it until Monday and the backup with the correct data would be gone because it was overwritten on Friday night.

I create versioned backups, a snapshot of the day and keep a copy of each one. Yes, it does take up a lot of disk space and it probably could be done better than I do it, but it has been very helpful in a couple of cases where people deleted something they needed and didn't realize it until a month later.

I have a script that creates an archive with the day's date as its name.

-Matthew

One could do this by making a script (or 7 scripts) that back up to different folders, each named after a day. Then you could use cron to run each script once a week, on a particular day.

For example:

Tuesday.sh would use rsynch to backup to /where/you/mounted/hdc/TUESDAY, and cron would run it every Tuesday night. 

That way you'd have the last week backed up, AND since you were using rsynch, if for some reason you didn't change a file for a week, you wouldn't have to copy it over again, so it would run faster.

---

