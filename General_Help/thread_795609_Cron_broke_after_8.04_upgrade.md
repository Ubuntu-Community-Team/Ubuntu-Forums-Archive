---
title: "Cron broke after 8.04 upgrade"
date: 2008-05-15
forum: General Help
---

### Post by solexious on 2008-05-15
Hello,

After I upgraded to 8.04 all the cron files that I have in cron.daily and cron.hourly are not running, I'm not sure about the other folders as I'm not using them. Cron jobs managed by crontab are running fine.

An thing I can do?

Thank you

Solexious

---

### Post by ibuclaw on 2008-05-15
Firstly, make sure all the cronjob files are executable.

```

cd /etc/cron.daily
ls

```

If all the files inside that folder are green, then they are executable.

Else, type in this (while still in the /etc/cron.daily folder)
```
sudo chmod +x *
```

And do that for all cronjob folders too:
```

cd /etc/cron.hourly
cd /etc/cron.weekly
cd /etc/cron.monthly

```

I'll get back to you in 1 minute on what else to do (my hourly jobs start at 11:00)

Regards
Iain

---

### Post by ibuclaw on 2008-05-15
Also, to verify that no cronjobs are running.

1) Make a script file.
ie:
```

#!/usr/bin/env bash
updatedb

```

2) Save it and mark it executable.
```
chmod +x updatedb.sh
```

3) Copy it to your Hourly folder
```
sudo cp updatedb.sh /etc/cron.hourly/
```

4) Edit your crontab file to execute that file sometime in the very near future (say, 2 minutes).
```
sudo gedit /etc/crontab
```

Find the line with "/etc/cron.hourly" and change it to:
```
00 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
```
00 is the minute of the hour (ie, 20 or 30 may be a good time to set it at by the time you read this.)

Save the cronjob file, and wait.

If you experience noise (or rise in activity) from your CPU at the time you set it, your cronjobs are working just fine! (as updatedb can be an intensive job).

Regards
Iain

---

