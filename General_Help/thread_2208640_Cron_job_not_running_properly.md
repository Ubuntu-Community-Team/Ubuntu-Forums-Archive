---
title: "Cron job not running properly"
date: 2014-03-01
forum: General Help
---

### Post by thnewguy on 2014-03-01
I have a cron job set up on my machine at home that should search through the /var/log directory and delete any compressed log files. The cron job is set to run once per month. Here is the entry in the /etc/crontab file

```

39 2 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```

And here is the script, which is saved as /etc/cron.monthly/clear-logs
The following script is owned by root and has the rwx permissions of 755.

```

#!/bin/bash
/usr/bin/find /var/log -name "*".gz -exec rm {} \;

```

I checked my syslog file this morning and found that is looks like the monthly jobs had run on time.
```

Mar  1 02:39:01 kerri CRON[5969]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar  1 02:39:01 kerri CRON[5970]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly ))

```


However, looking in my /var/log directory I found all the files the script should have removed were still there. Running the command "sudo /etc/cron.monthly/clear-logs" caused the script to run and properly clean out the /var/log directory.

So here is my problem: The script works when run manually, the crontab job appears to be running on time (according to my log file) but when the script is called by cron it does not perform its function. Can anyone suggest something I am missing here?

Update: I found a workaround, if not a proper solution. I edited root's crontab and added the entry to run the clear-logs script from there. The job runs fine as root and properly clears out the unwanted log files. Not sure why it does not work when run from the system-wide crontab, but it works fine when run from root'scrontab.

---

### Post by Lars Noodén on 2014-03-01
An alternate method of cleaning up log files would be to put a configuration file in /etc/logrotate.d/ telling [logrotate](http://manpages.ubuntu.com/manpages/saucy/en/man8/logrotate.8.html) which files to go after.

---

