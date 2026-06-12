---
title: "Ubuntu 14.04 random X server crash, reboot"
date: 2015-09-17
forum: General Help
---

### Post by lcl on 2015-09-17
Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

I would like to know the cause then hopefully the cure of it.  I read

/var/log/syslog - System wide logger, use tail /var/log/syslog or less /var/log/syslog
/var/log/kern.log - Kernel log, same as above
/var/log/*

and when I do 
```

last | head -n 50 

```

I finally see the word crash and the time

But in the above logs, I just don't know what to look for, I don't think I see the word 'crash' or similar wording.  What exactly should I look for in the log files?  The problem is really random reboot, there is no freeze, it just reboots itself.

I appreciate any direction.

Thanks.

---

### Post by ian-weisser on 2015-09-17
If it's a real reboot (manufacturer's poweron logo and POST, then GRUB, then splash screen, then login screen), then start looking at hardware causes. The worst software crash would cause Ubuntu to freeze or become otherwise unresponsive with power on, not to poweroff nor to reboot.

If it's not a real poweroff/poweron reboot, but you're losing all work and being returned to the login screen (no mfgr logo, no GRUB), then the X server is crashing. That might be hardware or software, and the logs in /var/log/syslog, var/log/dmesg, and var/log/Xorg.0.log are your first steps for logged clues.

---

### Post by lcl on 2015-09-17
thank you.
Mine is the 2nd scenario, a reboot without any manufacturer logo or GRUB.  I tried to look for any hint in those logs, I just don't see anything.  What exactly would be the wording in those file for a crash.
I did a 
```

last | head -n 50 

```and locate the time of crash at 21:06, for one, then I did a 
```

cat /var/log/syslog | grep 21:06 | more

```
; it returns some rows but I don't see any fail or crash.  Same with other logs.

What should I looking at or for in the logs?  I also looked at the /var/log/Xorg.0.log not a clue.

Thank you for any direction.

---

### Post by ian-weisser on 2015-09-18
A reboot is very different from an X crash, and requires different skills to diagnose and fix.
Please correct the thread title to reflect your actual problem, so you attract the proper help.

There is no single event or item or wording to look for.
You look for causes within a few seconds in the logs.
Feel free to post the sections of all three logs here. [Use [code] tags]("http://ubuntuforums.org/showthread.php?t=1189729") for clarity, and to keep the formatting.

---

