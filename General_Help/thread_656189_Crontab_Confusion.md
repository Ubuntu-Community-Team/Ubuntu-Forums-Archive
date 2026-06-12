---
title: "Crontab Confusion"
date: 2008-01-02
forum: General Help
---

### Post by driggins on 2008-01-02
So crontab has me baffled. I'm attempting to rsync from one volume to another, once a day.

I'm assuming this command needs to be executed as root to ensure that all files are copied, regardless of permissions. Based on this, I am editing the root crontab with the following command:

> sudo crontab -e

This file has two lines:
> # m h  dom mon dow   command
0 0 * * * rsync -r -t -v --progress -u /media/data/Shared/ /media/backup/Shared/


After editing, I press CTRL+O to "write out" the file. I allow it to write out to the default file name: 
> /tmp/crontab.19BMIG/crontab

Then, I press CTRL+X to exit. Voila. Done.

I'm sure that my rsync command works because it executes from the command line without a problem. I'm also sure that this cron job is not executing.

Any ideas?

---

### Post by cdenley on 2008-01-02
I'm not sure why crontab -e is writing to a temporary file, but maybe you should try creating a script in /etc/cron.daily.

---

### Post by sciencewhiz on 2008-01-02
try putting the full path to rsync (probably /usr/bin/rsync, but I'm not at my ubuntu computer right now).

Like cdenley said, I use cron.hourly/daily/monthly instead of crontab.

To use those, make a file called backup.sh (or something like that) in /etc/cron.daily with the following contents:

```
#!/bin/bash
/usr/bin/rsync -r -t -v -u /media/data/Shared/ /media/backup/Shared/
```

Note:  It probably doesn't make sense to use --progress when it's run in cron.

---

### Post by lgambett on 2008-01-02
The procedure you used is correct; have you checked (eg with ps aux) if cron fired at midnight as you wrote in the user crontab ?

---

### Post by driggins on 2008-01-03
Thanks, Sciencewiz. I've used your idea and will see if it works this evening.

---

### Post by driggins on 2008-01-10
Sciencewiz, I tested the script using "sudo sh /etc/cron.daily/backup.sh" and it executes perfectly.

Using lgambett's suggestion, I looked at the log using "ps aux" and note that the script has not executed. I can further verify that it has not run because it found many new files just now to backup.

Any idea on why this script is not being run?

Thanks,
daryl

---

### Post by KCPokes on 2008-01-10
> **driggins said:**
> Using lgambett's suggestion, I looked at the log using "ps aux" and note that the script has not executed. I can further verify that it has not run because it found many new files just now to backup.

Any idea on why this script is not being run?

Thanks,
daryl

I'd assume its because of PATH.  It is the single biggest hiney biter when it comes to cron jobs.  Because it runs command line does not mean it'll run when called from cron.  Be sure to fully qualify all calls with the full path.  My assumption, at this point, is due to the fact that rsync is not found in the path, as was stated above.

---

### Post by driggins on 2008-01-10
Yep. I incorporated the suggestion to use the full path already. Here's the entirety of the script called "backup.sh":
> #!/bin/bash
/usr/bin/rsync -r -t -v -u /media/data/Shared/ /media/backup/Shared/

Any other ideas as to why it's not running?

---

### Post by PinkFloyd102489 on 2008-01-10
Im having a similar problem, except Im not running rsync directly. I installed a crontab (it went to a tmp file also) with a custom script that I placed in /bin.

Im wondering if it'll run (isnt scheduled until Sunday).

---

### Post by sunzaru on 2008-01-26
learning crontab.

Idea:
I have a sound i want to play (in the background w/ no gui) at minute 30 of every hour.

Solution:
/etc/crontab  (looks like this SHOULD do it)

```

sudo gedit /etc/crontab
30 * * * * sunzaru /usr/bin/mplayer /backup/NameOfSong.mp3

```

yet.. it doesn't play.  it works fine if i do "  /usr/bin/mplayer /backup/NameOfSong.mp3  "

---

