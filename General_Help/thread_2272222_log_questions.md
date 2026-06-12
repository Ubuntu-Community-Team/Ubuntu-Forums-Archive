---
title: "log questions"
date: 2015-04-05
forum: General Help
---

### Post by iason on 2015-04-05
I am writing a auth log parser as a means to contribute to a tool and to learn linux logging better. I have been reading up on syslog and log facilities and was wondering if what is in auth.log will also be duplicated in syslog.log? Does it just make sense to only parse syslog and not other facility specific log files, assuming I want to grab all facility logs? I guess what I am asking is there ever a time that there will be a unique log instance found in auth.log that will not also be included in syslog?

in addition, when looking at a log file such as auth.log. is there a sure way of telling what facility is being used other than identifying by the log file name and path. Just thinking in terms of log identification when dealing with moved, renamed or deleted log files.

Please correct any misguide thoughts i've expressed.

---

### Post by dino99 on 2015-04-05
ubuntu have chosen systemd now , so journalctl is collecting all the processes

---

### Post by iason on 2015-04-05
This is very good to know, this is a good next project.  My interest is in forensics, to my knowledge the majority of servers have yet to implement systemd.

---

