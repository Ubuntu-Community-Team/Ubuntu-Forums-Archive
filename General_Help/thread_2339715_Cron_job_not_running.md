---
title: "Cron job not running"
date: 2016-10-12
forum: General Help
---

### Post by ajmannen on 2016-10-12
Hello, I've made a cron job to back up my database. But it does not run, I've tried changing the time it run and let it be for two days, but nothing happens.

My crontab

```
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
38 01 * * *  sh /home/andreas/sqlbackup.sh

```

The file, with edited username and password and database name. File runs fine on it's own so I manually run it now.

```

#!/bin/bash
mysqldump -u USER -pPASSWORD DATABASE > /home/andreas/backUp/HiOAGaming_$(date "+%b_%d_%Y_%H_%M_%S").sql

```

EDIT: I made the crontab job by using "crontab -e" from my user, the file is in my home folder.

Thank you for all replies! :)

---

### Post by TheFu on 2016-10-12
cron doesn't have much environment. You need to set whatever is required.
A simple backup script:```

#!/bin/bash
DB_NAME=redmine
BACKDIR=/root/backup/
/usr/bin/mysqldump -u root \
    -p`cat ~root/bin/$DB_NAME.passwd.root` $DB_NAME | \
    gzip > $BACKDIR/${DB_NAME}_`date +%Y%m%d`.gz
find  $BACKDIR -type f -name $DB_NAME\* -atime 60 -exec rm {} \;
```

Then just make certain that the place where the DB is dumped is included in the major backups for the system where you get /etc/ and /home and all the other important stuff like lists of installed packages, etc.  As you can see, I remove any DB backup files over 60 days old.

Usually backups should be run as root, so there aren't any permissions issues on reading protected files in /etc/ and elsewhere.

---

