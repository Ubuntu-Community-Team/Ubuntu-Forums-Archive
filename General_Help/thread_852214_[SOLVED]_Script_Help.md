---
title: "[SOLVED] Script Help"
date: 2008-07-07
forum: General Help
---

### Post by Titan8990 on 2008-07-07
I am trying to make a script for a weekly cron job. What it will do is tar all my log files from other cron drops and drop them into an archive. What I am trying to do is have the files named after the date. I have done this in another script but it was a script that I modified and not one I wrote from scratch. It's format looks like this:

THEDATE=`date '+%Y%m%d-%s'`
LOGFILE=/var/log/backup/rsync-$THEDATE.log

I have been messing around on the command line trying to get tar to tar a file and name it the date but I have yet to have any luck.

Anyone have suggestions on how to do this?

---

### Post by ghostdog74 on 2008-07-07
so what seems to be the problem? to rename the file, use mv command
```

mv $oldfile $newfile

```

---

### Post by Titan8990 on 2008-07-07
Sorry, what I am asking is the correct syntax to getting the date in the file name. When I tried something similar to what is show tar tried to make a multiple file archives. I couldn't even deleted the tar throught the shell, I had to sudo nautilus to remove it .

root@einstein:/var/log/backup# tar -xvf `date` *
tar: Mon: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
root@einstein:/var/log/backup# tar -xvf 'date' *
tar: date: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
root@einstein:/var/log/backup# tar -xvf `'date'` *
tar: Mon: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by Barriehie on 2008-07-07
I use this:

```

tar cvpzf /home/barrie/disk/backup-files/bup**$(date +%m%d%y)**.tgz

```It then generates bupMMDDYY.tgz

Barrie

Edit: See **man date** for more options on formatting.

---

### Post by Titan8990 on 2008-07-07
Exactly what I was looking for, thanks.

---

### Post by Barriehie on 2008-07-07
> **Titan8990 said:**
> Exactly what I was looking for, thanks.

:) Glad to help.  Don't forget to mark the thread solved!

Barrie

---

### Post by Titan8990 on 2008-07-07
If anyone is insterested this is what my script looked like in the end and it worked like a charm:

```
#! /usr/sh

tar -cvf $(date +%m%d%y).tgz /var/log/backup/*

mv $(date +%m%d%y).tgz /var/log/backup/oldlogs

rm /var/log/backup/rsync*
```

---

### Post by ghostdog74 on 2008-07-07
> **Titan8990 said:**
> If anyone is insterested this is what my script looked like in the end and it worked like a charm:

```
#! /usr/sh

tar -cvf $(date +%m%d%y).tgz /var/log/backup/*

mv $(date +%m%d%y).tgz /var/log/backup/oldlogs

rm /var/log/backup/rsync*
```

no need for mv, if you specify the path in tar
```

tar cvf /var/log/backup/oldlogs/$(date +%m%d%y).tgz  /var/log/backup/*

```

---

