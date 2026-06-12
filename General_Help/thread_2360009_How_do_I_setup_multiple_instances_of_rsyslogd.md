---
title: "How do I setup multiple instances of rsyslogd?"
date: 2017-04-30
forum: General Help
---

### Post by anewec on 2017-04-30
[TABLE="class: tborder, width: 100%, align: center"]
[TR]
[/TR]
[TR]
[TD="class: alt2"]I'm trying to set up multiple instances of rsyslogd to listen to multiple ports for data. Below is what I have done:

Copied /etc/rsyslog.conf to /etc/customrsyslog.conf
- Set up listening port
Copied /etc/init.d/rsyslog to/etc/init.d/custom-rsyslog

Updated the following in /init.d/customrsyslog: 
NAME= custom-rsyslog
RSYSLOGD_PIDFILE = /var/run/custom-rsyslog.pid

Copied /etc/default/rsyslog to/etc/dafault/custom-rsyslog
Updated the following in/default/custom-rsyslog
RSYSLOGD_OPTIONS="-f /etc/custom-rsyslog.conf"
RSYSLOGD_PIDFILE="-i /var/run/custom-rsyslog.pid"

When I start rsyslog: service custom-rsyslog start

 I get this:
* /usr/sbin/rsyslogd is not running

I'm running Ubuntu 14.04.

Is there something else I should be doing? Dont know what I'm missing.

Thanks in advance![/TD]
[/TR]
[TR]
[TD="class: alt2"][/TD]
[/TR]
[/TABLE]

---

