---
title: "crontab entry not running"
date: 2008-07-09
forum: General Help
---

### Post by dchurch24 on 2008-07-09
Hi all,

Whilst not a complete linux noob, I cannot seem to get my cron job to run.

I have set up a few on my [remote] web server and one for a friend - both do the same thing, run a script that rars all the files on the server and FTPs them to an external site for backup.

I am trying to do a similar thing at home, yet the job never seems to run.

> 
# m h  dom mon dow   command
* * * * * /home/dave/Scripts/backup.sh


At the minute I am just trying to get it to run every minute - just so I can see it working, but nothing happens.

If I run the backup.sh script from the terminal it runs fine.

What have I done wrong?

Thanks in advance!

EDIT: PS. There is a new line after the end of the backup.sh.

---

### Post by justleen on 2008-07-09
try ```

# m h dom mon dow command
*/1 * * * * /home/dave/Scripts/backup.sh

```

---

### Post by dchurch24 on 2008-07-09
Thanks for the quick reply!

Sadly though, it still doesn't run.

---

### Post by justleen on 2008-07-09
if you place this in cron:
```

*/1 * * * * logger "testing cron"

```
can you then see (after a few mins) "testing cron" at the end of /var/log/messages ?

---

### Post by dchurch24 on 2008-07-09
Hi,

I added that line, then checked the messages about 5 mins later, but the text is not there.

After doing a ps -A |grep cron

I can see cron in the list - not crond though.

---

### Post by rogier.de.groot on 2008-07-09
Running a backup script EVERY minute? That'll overload your system pretty fast if the script requires more than a minute to run... Slow it down a little.
Comment out everything else, reboot or restart crond, check that there are NO cron jobs left running (rebooting is best for that). Then try adding that logger line again.
Good luck!

---

### Post by justleen on 2008-07-09
thats weird.. 

crond shouldnt show up in ps though, just cron - so thats fine.

just running ```
logger "any text here" 
``` does show up in messages I assume?

restart /etc/init.d/cron, does that spew out errors?

PS: rogier.de.groot is quite right. a backup script every minute can clogg up your system. for now try the logger entry every minute, when that works, adjust the schedulded time.
You can check how long something runs with "time"
```

 # time (/usr/local/bin/inc_backup.sh )
/bin/tar: Removing leading `/' from member names

real    0m8.562s
user    0m8.161s
sys     0m0.388s

```

---

### Post by dchurch24 on 2008-07-09
> **rogier.de.groot said:**
> Running a backup script EVERY minute? That'll overload your system pretty fast if the script requires more than a minute to run... Slow it down a little.
Comment out everything else, reboot or restart crond, check that there are NO cron jobs left running (rebooting is best for that). Then try adding that logger line again.
Good luck!

Hi, I'm only running it every minute until I know that it's working.

It should run at 1am every morning, but yesterday was the first day since the reinstall, and it didn't run, so rather than wait until 1 am again I am running it every minute so that I can test it.

Once it's working it'll be every 24 hours once again.

How do I restart crond?

---

### Post by dchurch24 on 2008-07-09
Just running logger "some text" does work and does put an entry in the messages file.

I have added that to the crontab in place of my .sh script, and will come back in a few minutes to say if it has worked or not.

---

### Post by dchurch24 on 2008-07-09
Aha! That does put the message in the message folder every minute, so the problem must be with my script - which is odd as when I run it manually it runs fine (in fact is running now).

---

### Post by dchurch24 on 2008-07-09
...and so I changed it back to the script and it seems to be working now.

Thank you so much to the pair of you.

EDIT: No it's not working, bugger.  Would I see any output from the script, i.e. would it shell a terminal session.

The reason I say it's not working is because the drive isn't working (or spinning, or making a noise) - which it does if it's in use.

---

### Post by justleen on 2008-07-09
the logger in crontab was not working earlier, so you said?

if its working now, does that mean the backup runs too ?

are you using full paths in your backup script? 
try adding $PATH to you script
```
 echo $PATH
```
copy that, and paste in your script
```

export PATH=<paste> 
```

---

### Post by justleen on 2008-07-09
ah, good on you.. must have been cron itself then (assuming you did a restart/reboot)

---

