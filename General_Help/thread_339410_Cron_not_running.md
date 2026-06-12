---
title: "Cron not running"
date: 2007-01-15
forum: General Help
---

### Post by walmartshopper67 on 2007-01-15
I'm running edgy (up to date) - and the stuff in any of my cron directories (cron.weekly, cron.daily, cron.weekly, and cron.hourly) does NOT run. There are no errors. I'm using the following test script in each directory (chmodded to 755, chowned to my username): 

#!/bin/bash
touch ~/TESTHOURLY.txt 

(with TESTDAILY, TESTWEEKLY, etc.)

in System, Administration, Services: I have "Actions Scheduler (anacron)" and "Actions Scheduler (atd)" both running. 

But nothing in those directories runs on its own. They DO run if i run the scripts by hand (i.e. /etc/cron.hourly/testfile.sh).

I'm having a tough time setting up any kind of backup plan, which i really feel uncomfortable not having here at school (i don't like to write my papers ONCE let alone again because i lost it.) Thank you SO MUCH for any help.

The following is my output from running 'sudo crontab -e' :

# m h  dom mon dow   command
# Run hourly cron jobs at 47 minutes after the hour:
55 * * * * /usr/bin/run-parts /etc/cron.hourly 1> /dev/null
#
# Run daily cron jobs at 4:40 every day:
40 4 * * * /usr/bin/run-parts /etc/cron.daily 1> /dev/null
#
# Run weekly cron jobs at 4:30 on the first day of the week:
30 4 * * 0 /usr/bin/run-parts /etc/cron.weekly 1> /dev/null
#
# Run monthly cron jobs at 4:20 on the first day of the month:
20 4 1 * * /usr/bin/run-parts /etc/cron.monthly 1> /dev/null

---

