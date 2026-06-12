---
title: "Ubuntu 6.06 Crashing!!!"
date: 2006-07-24
forum: General Help
---

### Post by tgarza on 2006-07-24
Ubuntu 6.06 is crashing constantly. The machine gets totally frozen.  I am not able to use the desktop, I cannot check task manager, everything freezes without an error message.

I have not been able to execute openoffice.  It always freezes when I try to browse the list of processes in the system monitor.  Firefox also freezes often.

However, I can run GIMP, GAIM, the whole set of accesories, administrative options and preferences without crashing the machine.

I have ran several memory tests, and it has not showed errors.

I need some feedback on how to correct this problem.

Thanks much, TGarza

---

### Post by T700 on 2006-07-24
Are the specific applications which crash the OS?  Was it *ever* running correctly?  If it was running properly, what changed just before the problem?  What new software was installed, config files tweaked, dependencies removed?

Paul

---

### Post by philippe_carlo on 2006-07-24
It may be interesting to take a peek at or near the end of the following files, after rebooting from such a freeze:

/var/log/kern.log.0
/var/log/syslog.0
/var/log/messages.0
/var/log/Xorg.0.log

---

### Post by twotonz on 2006-07-24
Hi,
Just a thought, do you have vmplayer installed? Some people have experienced complete freezes due to certain vmnet interfaces going haywire. A dirty workaround is to stop vmplayer-services as long as you are not useing it.

Love and Peace (to all)
anthony

---

### Post by The Noble on 2006-07-24
Aye, I had Dapper freeze on me when I used VMplayer from the repos. At least a temporary fix is to reinstall it. I think it is a problem with a kernel update. Happened when we moved to the latest Kernel, so I just reinstalled and it worked great again.

---

