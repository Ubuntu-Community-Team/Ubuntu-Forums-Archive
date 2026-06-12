---
title: "Are logs in /var/log/ automatically managed?"
date: 2014-05-30
forum: General Help
---

### Post by sim085 on 2014-05-30
Hello,

First of all is it best practice that an application saves it's log file in */var/log*? Or this is meant only for OS logs? 
Besides, does saving my log file in /var/log provide me with some additional service (ex: auto compress or so)?

---

### Post by slickymaster on 2014-05-30
**/var/log **log files from the system and various programs/services, specially login and syslog. Files in /var/log can often grow indefinitely, and may require cleaning at regular intervals. Something that is now normally managed via log rotation by logrotate. This utility also allows for the automatic rotation compression, removal and mailing of log files. Logrotate can be set to handle a log file daily, weekly, monthly or when the log file gets to a certain size. Normally, logrotate runs as a daily cron job.

---

### Post by sim085 on 2014-05-30
Thank you. So I have to search on how to set up Logrotate. Thank you for pointing me in the right direction.

> **slickymaster said:**
> **/var/log **log files from the system and various programs/services, specially login and syslog. Files in /var/log can often grow indefinitely, and may require cleaning at regular intervals. Something that is now normally managed via log rotation by logrotate. This utility also allows for the automatic rotation compression, removal and mailing of log files. Logrotate can be set to handle a log file daily, weekly, monthly or when the log file gets to a certain size. Normally, logrotate runs as a daily cron job.

---

### Post by ian-weisser on 2014-05-30
> **sim085 said:**
> First of all is it best practice that an application saves it's log file in */var/log*?

Generally, yes...but there are exceptions.
/var/log is appropriate if it's a systemwide or multiuser service, if multiple processes are expected to write to the same log, or if the service uses rsyslogd (the system logging daemon) for writing log output. One would expect most single-user, single-process services to log to /home/$user/$application_name.log or someplace similar.

logs in /var/log are generally expected to use -or at least play nicely with- rsyslogd and logrotate. It's not required, but is expected behavior.

> **sim085 said:**
>  does saving my log file in /var/log provide me with some additional service (ex: auto compress or so)?

The most important service is the system logging daemon. Your applications can write to it instead of the logfile directly.

The other important service is logrotate, which keeps the log size manageable.

---

### Post by slickymaster on 2014-05-30
> **sim085 said:**
> Thank you. So I have to search on how to set up Logrotate. Thank you for pointing me in the right direction.

In a terminal window run the following```
man logrotate
```[URL="https://www.digitalocean.com/community/articles/how-to-manage-log-files-with-logrotate-on-ubuntu-12-10"]
How To Manage Log Files With Logrotate[/URL][URL="http://linuxers.org/howto/howto-use-logrotate-manage-log-files"]
Howto: Use logrotate to manage log files[/URL]

---

