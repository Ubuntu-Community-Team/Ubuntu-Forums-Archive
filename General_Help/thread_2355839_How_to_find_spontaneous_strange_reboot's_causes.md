---
title: "How to find spontaneous strange reboot's causes"
date: 2017-03-17
forum: General Help
---

### Post by pietrob71 on 2017-03-17
Hi guys, I've got a VPS with ubuntu 16.04 64bit:
```
uname -a
Linux 135764 2.6.32-042stab094.7 #1 SMP Wed Oct 22 12:43:21 MSK 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Using cron, I have set the system's reboot at 06:00:00 of each day, but sometimes there's a system's reboot at an apparently random time. I would like to understand, why this happen.

At now, the last system reboot is: Mar 16 22:23
```
who -b
         system boot  Mar 16 22:23
```

I've take a look at /var/log/syslog at Mar 16 22:23, but I can't understand the reboot's reasons, so I thought to make a post with syslog as attachement, hoping someone can help me.

Thanks in advance
Peter

---

### Post by ajgreeny on 2017-03-17
I can not find anything obvious in that log, but I am not much of an expert in searching such logs for clues.

However, does your machine get hot causing the reboot to save hardware damage.

I am also surprised to see you are using an old 2.6.32 kernel in 16.04.  Why is that, any idea?
It could be at least part of your problem, so it is definitely worth making sure your system is fully updated and running the default 4.4.0-67 kernel.

---

### Post by pietrob71 on 2017-03-17
> **ajgreeny said:**
> 
I am also surprised to see you are using an old 2.6.32 kernel in 16.04.  Why is that, any idea?


It's a VPS, so I can't choose the kernel version.

---

### Post by ajgreeny on 2017-03-17
> **pietrob71 said:**
> It's a VPS, so I can't choose the kernel version.
I will have to take your word for that as I do not know anything about using a VPS.
What about the overheating possibility?

---

