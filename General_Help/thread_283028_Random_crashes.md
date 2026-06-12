---
title: "Random crashes"
date: 2006-10-23
forum: General Help
---

### Post by jamyskis on 2006-10-23
Hi all,

I've recently been having problems with total crashes of my Ubuntu system. It's a dual-boot Ubuntu 6.06/Windows XP Pro system. 

Both OS's started crashing around the time that the NVIDIA security advisory was issued. Windows would hold up for on average 30 minutes, Ubuntu for 10. 

Originally I put this down to hardware issues, so I took my computer apart, put it together again, ran Memtest86+ (no errors after 51 passes, safe to say that it's not bad memory), checked the CPU temperature right after a crash (57-60, pretty normal) and monitored the graphic card temperature under both OS's - which never reached above 92. I also ran a hard drive scan under Windows, which returned no errors.

Anyway, after playing around with Windows, I managed to break it with no hope of return and was forced to reinstall. Whether it was a loose card or bar of memory, or something wrong with Windows I will never know, but it seemed to have fixed the problem - Windows now stays relatively stable (at least for Windows, anyway).

Ubuntu on the other hand insists on crashing. I've thought that maybe my computer was being compromised from using the nvidia (proprietary) driver, as I had heard that the proof-of-concept code provided could be used to remotely crash a PC. Thinking this, I switched to the nv driver, which made no difference whatsoever.

From a brief search of "crashes" in this forum, I see that a number of people are experiencing the same problem with Dapper. Has anyone had any luck on finding out where these crashes come from?

---

### Post by John.Michael.Kane on 2006-10-23
When your talking about your machine crashing does it hard lock?

Most crashes leave an end user with some log file depicting what happened. have you looked at them?

Also machines "crashing" can happen cause of buggy software/hardware issues not related to only memory. 

Is this machine over clocked?

Are you running any addons like xgl/compiz or beryl?

---

### Post by jamyskis on 2006-10-23
> When your talking about your machine crashing does it hard lock?

It does indeed.

> Most crashes leave an end user with some log file depicting what happened. have you looked at them?

Again, I have indeed. I've searched through every logfile under /var/log and I can't find anything that would suggest why it randomly locks up.

> Is this machine over clocked?

No.

> Are you running any addons like xgl/compiz or beryl?

I did on my previous installation of Ubuntu. Endless playing around with stuff I didn't really understand forced a reformat and reinstall of Ubuntu, and it's been since then that the problems have occurred.

---

