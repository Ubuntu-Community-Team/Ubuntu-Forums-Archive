---
title: "rsyslogd does not update /var/log/syslog"
date: 2014-05-03
forum: General Help
---

### Post by odror on 2014-05-03
OS: ubuntu 14.04

rsyslogd was working fine updating correctly /var/log/syslog.

I have installed syslog-ng and then removed it. As a result rsyslog was removed and then re-installed.

Since this change I am not getting updates in /var/log/syslog

I am using the default setup. Rsyslogd is running it is updating other log files, but not the syslog file.

When running  /usr/sbin/rsyslogd -c3 -dn

I get the following error: > rsyslogd: Could no open output pipe '/dev/xconsole': No such file or directory [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]


I commented the xconsole lines in /etc/rsyslog.d/50-default.conf

I am still not able to get updates in the syslog file.

My setup is the default setup. Somehow the instalation of the syslog-ng did something. 

Any help will be appreciated

Thanks

---

### Post by Habitual on 2014-05-03
did you restart rsyslogd?

---

### Post by odror on 2014-05-03
Yes. It updates all the log files, except for syslog.

---

### Post by odror on 2014-05-04
The problem is solved. When suslog-ng was installed it changed to owner of syslog and kern.log root root from syslog. All I had todo was to change the ownership back to syslog.

---

### Post by Habitual on 2014-05-07
That explains why my removal of rsyslog showed exactly the same symptom!
I just nuked it to orbit as it was zero bytes.

---

### Post by Seth-666 on 2015-01-25
i don't understand ... i littel tip ? :( how and what can i do ? 

> syslogd-2039	Could no open output pipe '/dev/xconsole': No such file or directory [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]


---

