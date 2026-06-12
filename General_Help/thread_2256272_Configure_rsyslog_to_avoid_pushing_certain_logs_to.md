---
title: "Configure rsyslog to avoid pushing certain logs to /var/log/messages"
date: 2014-12-11
forum: General Help
---

### Post by sudharshan-rrk on 2014-12-11
[COLOR=#000000][FONT=Arial]Hi,

I'm using rsyslog to track the logs of my application server so that I can push these logs to loggly. The problem is, rsyslog is logging all logs to /var/log/messages. I only want the error logs from the application server to be logged. Is there any way to avoid this? Can I filter out certain messages in /etc/rsyslog.conf so that these are not pushed to var/log/messages?

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]I tried adding the following lines in rsyslog.conf:
[/FONT][/COLOR]
if $programname == 'programName' then {
*.err                                                 /var/log/messages
} else {
*.info;mail.none;authpriv.none;cron.none                /var/log/messages
}

[COLOR=#000000][FONT=Arial]However, upon restarting rsyslog, I see the following error:
[/FONT][/COLOR]
Dec 11 08:01:46 <hostname> rsyslogd: the last error occured in /etc/rsyslog.conf, line 37:"if $programname == 'programName' then {"
Dec 11 08:01:46 <hostname> rsyslogd: warning: selector line without actions will be discarded
Dec 11 08:01:46 <hostname> rsyslogd-3000: unknown priority name "" [try [http://www.rsyslog.com/e/3000](http://www.rsyslog.com/e/3000) ]
Dec 11 08:01:46 <hostname> rsyslogd: the last error occured in /etc/rsyslog.conf, line 39:"} else {"
Dec 11 08:01:46 <hostname> rsyslogd: warning: selector line without actions will be discarded
Dec 11 08:01:46 <hostname> rsyslogd-3000: unknown priority name "" [try [http://www.rsyslog.com/e/3000](http://www.rsyslog.com/e/3000) ]
Dec 11 08:01:46 <hostname> rsyslogd: the last error occured in /etc/rsyslog.conf, line 41:"}"
Dec 11 08:01:46 <hostname> rsyslogd: warning: selector line without actions will be discarded

[COLOR=#000000][FONT=Arial]I suppose my version of rsyslog (5.8.10) doesn't support if / else. Is there any other way to do this? Or can I update rsyslog without deleting any of my existing configurations?[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-12-12
Yes, you can filter messages before they hit the syslog.

The easiest way is to add a file to /etc/rsyslog.d/
It's just like editing /etc/rsyslog.conf, but easier to find again, and easier to turn on/off as needed.

I haven't seen a $programname in syslog before - it would sure be a lot easier if applications were required to include their name.
Don't use shell script (if/then) trying to filter rsyslog - the syntax is quite different since it's only match/reject logic.
See man rsyslog.conf for a _lot_ of information.
Or, see [http://www.rsyslog.com/doc/rsyslog_conf_examples.html](http://www.rsyslog.com/doc/rsyslog_conf_examples.html) for some very good, easy examples.

Usually, I look to see if the application has an option to log someplace else first. That's easiest.
Then, I look to see if the application's log output has something recognizable I can use in a rsyslog.conf rule.

---

