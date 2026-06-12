---
title: "ClamAV logging"
date: 2005-06-23
forum: General Help
---

### Post by msisamonopoly on 2005-06-23
My /etc/clamav/clamd.conf file says to log to

/var/log/clamav/clamav.log

It does this. But it also logs a record of every file that it scans in

/var/mail/<username>

Questions
i. Anyone know how I can get it to log this info elsewhere?

ii. Anyone know how to set up logrotate to regularly flush the /var/mail/<username> file?
It currently has a log of stuff back to first installation of Ubuntu that would be useful to archive, but only keep last week of stuff in current /var/mail/<username> file.

tvm

---

### Post by elvis on 2005-06-24
"man clamd.conf" lists all of the possible options you can use.  Investigate the ones pertaining to turning on/off syslog features, and being quiet.

clamav-milter is the package that deals with mail scanning.  It is started via the options in /etc/default/clamav-milter.  For instance, I add the "--quiet" flag to stop clam reporting infected emails.

---

### Post by msisamonopoly on 2005-06-24
[QUOTE=elvis]"man clamd.conf" lists all of the possible options you can use.[/QUOTE]

You are absolutely right!

tks

---

