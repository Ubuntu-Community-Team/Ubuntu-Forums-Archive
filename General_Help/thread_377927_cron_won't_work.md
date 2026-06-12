---
title: "cron won't work"
date: 2007-03-06
forum: General Help
---

### Post by Kiamo on 2007-03-06
I have added a couple jobs to my crontab and recently set up SMTP, and now I get e-mails for every job in there every time they should run saying Command not found.

Here is /etc/crontab:
```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/hdf/mysql/db1:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root run-parts --report /etc/cron.hourly
25 6    * * *   root test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily > /dev/null 2>&1
47 6    * * 7   root test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly > /dev/null 2>&1
52 6    1 * *   root test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly > /dev/null 2>&1
 1 6    * * *   root sh /usr/local/bin/reindex.sh > /dev/null 2>&1
30 4    * * 7   root sh /hdf/mysql/db1/backup.sh  > /dev/null 2>&1

```

I have tried without the > parts and tried removing the root user to no avail.

Here is an example e-mail I get:
```

Message 1:
From xxx  Sun Mar  4 17:17:01 2007
X-Original-To: xxx
From: xxx (Cron Daemon)
To: xxx
Subject: Cron <xxx> root    run-parts --report /etc/cron.hourly
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/home/justin>
X-Cron-Env: <LOGNAME=justin>
Date: Sun,  4 Mar 2007 17:17:01 -0600 (CST)

/bin/sh: root: command not found

```

They are all virtually identical for every command.


Any ideas what could be wrong?
edit: I have tried copy-pasting the commands to a term to verify, and they work just fine, so they are definitely there...

---

### Post by tribble222 on 2007-03-06
Go to a terminal and enter 'sudo crontab -e' and try entering your commands into the crontab that way instead of editing the file.  Just a guess.  Also, when you don't specify the root user, what error message gets emailed to you?  The error message you provided seems to show crontab trying to run the command "root" but it's not found.

---

### Post by Kiamo on 2007-03-07
> **tribble222 said:**
> Go to a terminal and enter 'sudo crontab -e' and try entering your commands into the crontab that way instead of editing the file.  Just a guess.  Also, when you don't specify the root user, what error message gets emailed to you?  The error message you provided seems to show crontab trying to run the command "root" but it's not found.
It says the same thing when I take the root part out.
I just used the crontab -e command and added the stuff, but it asked me where to save.. I backed up and overwrote /etc/crontab, but I'm not sure that's correct as when I sudo crontab -l it says "no crontab for root".
Hrm :(

---

### Post by tribble222 on 2007-03-07
When you leave the crontab by pressing ctrl-x, just hit enter when it asks you if you want to save and save it in the default location (will be something like /tmp/crontab.gApyu/crontab).

---

### Post by Kiamo on 2007-03-07
> **tribble222 said:**
> When you leave the crontab by pressing ctrl-x, just hit enter when it asks you if you want to save and save it in the default location (will be something like /tmp/crontab.gApyu/crontab).
It works now!  Thank you.  :)

---

