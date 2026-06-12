---
title: "Ubuntu 7.04 server running out of memory"
date: 2007-09-14
forum: General Help
---

### Post by NevilleS on 2007-09-14
Hey guys,

I'm having a bit of a problem with my Ubuntu server. I'm running 7.04 and there is a serious memory leak somewhere. Within a couple hours, my 512MB of RAM is full and the system kills off all the processes and enters into panic. First, I thought it was my applications (lighttpd, openssh, etc.) so I did a FRESH install and found that the vanilla (no LAMP, DNS, anything) install of Ubuntu 7.04 manages to eat all my memory. I'm not sure what could be causing this problem (I've tried killing any process I can) so I'm a bit lost. The only clue I have so far is that, on boot, I get several errors to do with my SATA drive that look like this: **failed to set xfermode**, with an error mask of 0x4. Any ideas?

---

### Post by p_quarles on 2007-09-14
Have you tried running "top" to see what process is eating up the most memory?

---

### Post by IcemanV9 on 2007-09-15
> The only clue I have so far is that, on boot, I get several errors to do with my SATA drive that look like this: failed to set xfermode, with an error mask of 0x4. Any ideas?
Sounds like a hdparm problem. Check /etc/hdparm.conf file.

Also, take a look at a few logs (/var/log), such as, message, dmesg, syslog & kern.log to figure out what is eating up the memory.

---

