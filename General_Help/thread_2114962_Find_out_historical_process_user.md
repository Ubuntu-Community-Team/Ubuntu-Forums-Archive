---
title: "Find out historical process user"
date: 2013-02-11
forum: General Help
---

### Post by matimont on 2013-02-11
Hi,

I have a monitoring service that tells me a process has been running 85% CPU for more than 7 minutes. Of course by the time I went to the log, I saw Process ID and couldn't find what user was running it (was a php5 process).

So, is there a way to identify a process ID in the past and who was the owner of the process??

Thanks!

---

### Post by Bufeu on 2013-02-11
There is not normally any way to recover the PID of a process after it's  removed from the process table.  Some process-accounting add-ons such  as **sar** might be able to provide you with this information.
[http://www.unix.com/unix-dummies-questions-answers/78777-pid-getting-processname-terminated-old-process.html](http://www.unix.com/unix-dummies-questions-answers/78777-pid-getting-processname-terminated-old-process.html)

---

### Post by Habitual on 2013-02-11
[http://collectl.sourceforge.net/](http://collectl.sourceforge.net/)

---

