---
title: "Anacrontab not working"
date: 2013-05-04
forum: General Help
---

### Post by bandito40 on 2013-05-04
Here is what my anacrontab file looks like.

```

# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

7	5	cron.weekly	php5 /var/www/mazda/backup.php
7	10	cron.weekly	php5 /var/www/mazda/ups_backup.php

```

My two php files run maybe once and then never run again.  I have tested running my php files manually from the shell where they work perfectly.  Anyone know what is going on here.

---

### Post by Cheesehead on 2013-05-04
First, you shouldn't duplicate job names ("cron.weekly") in your anacrontab. It will confuse when something fails and you need to use logs to figure out what happened. "cron.weekly" refers to the /etc/cron.weekly folder. Anacron runs the scripts in that folder (if needed) after startup, or weekly.

Failure-to-run is rarely a fault with cron or anacron. It's almost always one of the following:
a) Script doesn't use full path names
b) Script assumes or requires an environment variable that does not exist when the user is not logged in. Common with programs that require a display, or big complex programs

Running the script in a terminal window is a *different environment* than cron/anacron has access to. That's why a) and b) occur. Instead, run the script from cron and direct *all* output into a logfile. Methodically add "This step succeeded" log entries in your script so you can identify the failing line.

---

### Post by bandito40 on 2013-05-04
The script replicates a copy of a table in a database.  No pathnames are used and the script logs itself into mysql. I'll try making a line by line log to see what happens. What do I put in the place of cron.weekly?

---

### Post by bandito40 on 2013-05-04
I changed the cron.weekly to backup1 and backup2. Then changed the scripts to run daily 1 and 2 minutes after boot. File looks like this:

```

1	1	backup1 php5 /var/www/mazda/backup.php
1	2	backup2 php5 /var/www/mazda/ups_backup.php

```

Ran "sudo anacron" and both scripts ran with success.  Now I'll switch the scripts to run weekly and see what happens.

---

