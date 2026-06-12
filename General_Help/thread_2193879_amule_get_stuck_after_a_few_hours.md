---
title: "amule get stuck after a few hours"
date: 2013-12-15
forum: General Help
---

### Post by massimosoave on 2013-12-15
Ubuntu 12.04lts x64 /Ubuntu 13.10 x64
I am recently having continuous unexpected and (apparently) unmotivated crashes on amule 2.3.1 installed fron official repository on ubuntu 12.04 x64. The pc and OS does not have any apparent problem, only amule after a few hours of running gets stuck and after a while the program gets closed.
I tried to reinstall the system from scratch and even tried to install the newest release of ubuntu, but amule behaves always as told before. I may suppose that some recent updates in libs are conflicting with amule operation (because the problem appeared just a few weeks ago, before that amule runned perfectly well); unluckily the system did not send any error messages on creen or in /var.
Thanks for any info about it. Also info on HOW to gather information on problem would be very useful.

Max

---

### Post by bashiergui on 2013-12-17
See if this matches your situation.
[https://bugs.launchpad.net/ubuntu/+source/amule/+bug/1156582](https://bugs.launchpad.net/ubuntu/+source/amule/+bug/1156582)

If no logs are recording the crash then turn up the logging level in syslog & debug.

---

### Post by massimosoave on 2013-12-18
I did not receive any error messages on screen; if I should look for error messages in a particular log file can please tell me which file.
And in case how do I turn up the log level and where should I see the logs ?
 (sorry for my ignorance but I am not a linux advanced user)

Thanks

Max

---

### Post by bashiergui on 2013-12-18
Best to start at the beginning then.
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
Look at the application logs for amule. Post snippets of the logs if you can't figure out what they're saying.

---

### Post by massimosoave on 2013-12-19
Did not find any application logs for amule in var/log but found a crash report into var/crash; see attached files (divided in 3 parts and without mem dump due to attach limitations).
THX

Max

---

