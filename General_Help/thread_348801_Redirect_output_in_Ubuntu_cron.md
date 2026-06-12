---
title: "Redirect output in Ubuntu cron?"
date: 2007-01-29
forum: General Help
---

### Post by yam on 2007-01-29
I'm trying to back up a mysql database using cron. but I cannot get any STDOUT to write to a file.  On the command line I can easily dump the DB using:

    /usr/bin/mysqldump -u dbuser -pdbuserpassword exampledb > /home/dbuser/exampledb.sql

and the file exampledb.sql is created but the same line in crontab doesn't work.  What gives?

This example does work from my OpenBSD cron job, so I'm doubly confused.

---

