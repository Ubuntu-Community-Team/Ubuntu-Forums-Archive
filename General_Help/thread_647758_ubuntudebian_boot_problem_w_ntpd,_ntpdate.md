---
title: "ubuntu/debian boot problem w/ ntpd, ntpdate"
date: 2007-12-22
forum: General Help
---

### Post by movrshakr on 2007-12-22
There seems to be an endemic problem during boot with ntpdate and ntpd conflicting...usually resulting in ntpd not running.

See
[http://www.nnseek.com/e/comp.protocols.time.ntp/autostart_problem_at_boot_unde_rlinux_190473520t.html](http://www.nnseek.com/e/comp.protocols.time.ntp/autostart_problem_at_boot_unde_rlinux_190473520t.html)

and

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg376928.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg376928.html)

But I cannot sort out from these threads what the fix is.  Help, please as I have this problem.

Note...it is a good idea to run ntpdate before ntpd starts because if your hardware clock is more than 1000 sec (16 min) different from actual, ntpd will exit, and you will only know it from syslog.  Running ntpdate first (preferably followed by' hwclock --systohc' will ensure that doesn't happen.

Need help please.

---

