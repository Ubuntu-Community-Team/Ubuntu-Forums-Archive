---
title: "Suspecious log rotation and compression"
date: 2007-01-15
forum: General Help
---

### Post by nwiebe on 2007-01-15
Hi, I've written a program that does logging through syslog (facility local0).  The logs are supposed to be rotated through logrotate, but it looks like some other process might be rotating my logs.

I've configured syslog to send all local0 messages to /var/log/program.log.  This is from /etc/syslog.conf:

local0.*     /var/log/program.log

This part works fine, log messages show up in /var/log/program.log like I expect.  I also have configured logrotate to rotate this log.  This is what's in /etc/logrotate.d/program:

/var/log/program.log {
  create
  weekly
  rotate 26
  missingok
  nocompress
  nomail
  sharedscripts
  postrotate
    /etc/init.d/sysklogd restart
  endscript
}

When I manually force log rotation with "logrotate -f /etc/logrotate.d/program" things get rotated nicely like I expect.   /var/log/program.log is renamed to /var/log/program.log.1 (and .1 is renamed to .2, etc).  The log files are not compressed.

However, when the system is left alone for a few days I find that the log files are being rotated daily, even though I've got 'weekly' in the logroate options.  I also see files like /var/log/program.log.1.gz.  Which other processes could be zipping these log files?  

I've noticed that /var/log/syslog,messages, and kern.log  are rotated daily by /etc/cron.daily/sysklogd.  Looking at the script, it uses the syslogd-listfiles command to determine which log files to rotate daily.  When I run syslogd-listfiles manually I get:

root@thebox:~# /usr/sbin/syslogd-listfiles
/var/log/messages
/var/log/syslog
/var/log/kern.log

Which doesn't include the log file I'm interested in (/var/log/program), so it seems that this cron job isn't to blame, but the compression and daily log rotation fit with what this cron job does.  Can anyone suggest anything to check?  Why do we need savelog when we have logroate?

I'm using Ubuntu 6.06.1 LTS.

Thanks for your help.
Nathan Wiebe

---

