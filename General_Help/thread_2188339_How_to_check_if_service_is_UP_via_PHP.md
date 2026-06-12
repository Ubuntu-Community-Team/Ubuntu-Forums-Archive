---
title: "How to check if service is UP via PHP?"
date: 2013-11-16
forum: General Help
---

### Post by alek66 on 2013-11-16
I am trying to make a status web site, simple, and wanted to check the status of certain services, like if vsftpd, avahi, cups are running.

Any ideas?

---

### Post by tgalati4 on 2013-11-16
Some ideas:  [http://ubuntuforums.org/showthread.php?t=2166875&highlight=PHP+system](http://ubuntuforums.org/showthread.php?t=2166875&highlight=PHP+system)

More ideas:  [http://ubuntuforums.org/showthread.php?t=1712094&page=2&highlight=PHP](http://ubuntuforums.org/showthread.php?t=1712094&page=2&highlight=PHP)

---

### Post by SeijiSensei on 2013-11-17
I run this script on my servers every fifteen minutes from cron:

```

#!/bin/sh

LOG=/var/log/daemon-check.log

PROGS="sshd crond rsyslog httpd named ntpd [more daemons if appropriate]"

for prog in $PROGS
do
   progtest=$(ps aux --width=256 | grep $prog | grep -v grep)
   if [ "$progtest" != "" ]
   then
      echo -n `date` >> $LOG
      echo " $prog running" >> $LOG
   else
      /sbin/service $prog restart  >> $LOG 2>&1
      echo -n `date` >> $LOG
      echo " $prog *** RESTARTED ***" >> $LOG
   fi
done

```

The key line is the one that creates "progtest" by using "ps aux".  

This script is designed to restart daemons that have stopped for some reason.  You might also want to receive email notifications if a daemon is restarted.  If the machine has an SMTP listener running like Postfix or sendmail, add the line 

```
echo "Restarted $prog at $(date)" | mail -s "$prog RESTARTED!" you@example.com
```

just after the line that logs the restart, replacing "you@example.com" with your correct email address.

In PHP, you can run the "ps aux" command using the [shell_exec()]("http://php.net/manual/en/function.shell-exec.php") function.

---

