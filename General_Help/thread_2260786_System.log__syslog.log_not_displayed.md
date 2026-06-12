---
title: "System.log  syslog.log not displayed"
date: 2015-01-14
forum: General Help
---

### Post by afhx on 2015-01-14
I was working at the  terminal when I decided to empty the rubbish bin - on my dash  the rubbish bin is next to System.log.
Suddenly the system closed down and rebooted ( I have ubuntu14.04). Naturally, I went to System.log to find out what happened. I found the system.log had been removed and the dpkg.log had been wiped clean. Going to /var/log  I found the following entries:
rsyslogd changed groupid to 104 and userid changed to 101.
I really would like the System.log as it was before. Is this possible?. Also the  reason why this happened
Any  help would be appreciated as I use these logs regularly and System.log is a lot more convenient than going to /var/log

---

### Post by afhx on 2015-01-17
Each time  I boot up I get the same message as above. Checked rsyslog.d but userid and groupid not changed for the 50-default.conf file therein.. Can someone tells what the groupid and userid should be on gnome-system-log because I suspect that is where the changed has been applied. I know that rsyslog does not update syslog  and syslog's userid is 101. Do you think that re-installing gnome-system-log and rsyslog will rectify the problem.Would it be a good idea to clear the configuration files for these at the same time?.
I spend a lot of time of programming in C++ and Java  and find hard to keep up to date so that I am proficient in sorting problems when these arise with ubuntu.

---

### Post by afhx on 2015-01-25
Complete re-installation of gnome-system-log and rsyslog did not put things right

---

### Post by afhx on 2015-01-29
Even though I received no replies to this  query I am  marking this as solved since KSystemLog  is  a more than adequate replacement for gnome-system-log

---

