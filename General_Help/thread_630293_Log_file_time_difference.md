---
title: "Log file time difference"
date: 2007-12-03
forum: General Help
---

### Post by Footer on 2007-12-03
For some reason, the timestamp going in to my log files is off by 6 hours like this:

Dec  3 07:24:00 (current time on machine)
Dec  3 13:24:00 (log file time)

I'm talking about log files like /var/log/messages and /var/log/syslog.  I think that means the log files are using UTC time but not sure (I'm in the Central Time Zone).

Does anyone know where/how to change it so it reflects the 'current' time?

Thanks!

---

### Post by Footer on 2007-12-07
Hate to bump this but it's been 4 days and no response/opinions. Does ANYONE have any ideas about this?  It's really starting to bug me!  I'm running Kubuntu 7.10 if that helps.

Thanks!

---

### Post by Footer on 2007-12-07
Well, after a little more searching, I found this thread:

[http://ubuntuforums.org/showthread.php?t=519580&highlight=tzconfig](http://ubuntuforums.org/showthread.php?t=519580&highlight=tzconfig)

Reply #2 talks about setting UTC=no in: /etc/default/rcS which I did.  After a reboot, my log files timestamps now show the same as the local time.

I hope this helps others who may encounter this problem.  Apparently a rare problem since no one else seems to have experienced it!

Thanks!

---

