---
title: "kernel crash does not create dump"
date: 2014-08-05
forum: General Help
---

### Post by elias-rabi on 2014-08-05
Hi,

I have a Dell R620 server that crashes randomly..
I have installed linux-crashdump and rebooted.
And the crash kernel is loaded it appears.
```
# cat /sys/kernel/kexec_crash_loaded
1
```
But it crashed yesterday and there is no files in /var/crash.
I've attached a screenshot of a crash (this crash isn't from when the crash kernel was loaded).
What would be my next step? I need to figure out what is causing the crash.

/Raboo

---

### Post by tgalati4 on 2014-08-05
Perhaps that is not a kernel crash.  Linux expects perfect hardware.  Linux has a hard time dealing with faulty hardware.  Because the crash dump was not collected, I would suspect a power supply or motherboard issue.  Swap power supplies with a known working one.  Dell power supplies have known issues.  If you have dual power supplies, take them out and mark with a Sharpie as #1 and #2.  Put #1 in and run it for a while.  If it freezes, then replace it with #2 only.  If it stays up for a while, then you have narrowed down the problem.

---

### Post by elias-rabi on 2014-08-05
So a kernel or software crash will always create a dump?

---

