---
title: "Startup scripts (/etc/rc*.d)"
date: 2007-06-04
forum: General Help
---

### Post by Oleg Petrov on 2007-06-04
Hi All,

Unexpectedly, I realised that no scripts placed in /etc/rc*d/ are executed at startup at their corresponding run-levels. Moreover, I did not find anything here:
ls -la /sbin/ | grep rc
Before getting acquainted with Ubuntu, I dealt with Solaris primarily, and I have always made use of such scripts. Does Ubuntu utilize the same concept of run-level scripts or it is completely different here?

Thanks for advance.

---

### Post by blackened on 2007-06-04
Watch the short video at the bottom of this thread. [http://ubuntuforums.org/showthread.php?t=462195]("http://ubuntuforums.org/showthread.php?t=462195")

---

### Post by Jussi Kukkonen on 2007-06-04
> 
Unexpectedly, I realised that no scripts placed in /etc/rc*d/ are executed at startup at their corresponding run-levels.
That must be a mistake on your part, as they do execute. What may have fooled you is the default runlevel: it's rc2.
> Moreover, I did not find anything here:
ls -la /sbin/ | grep rc
I'm not familiar with Solaris, what did you expect to find? If it's the actual scripts, they can be found in* /etc/init.d/*

---

