---
title: "After a while, system will only respond after mouse movement."
date: 2008-05-01
forum: General Help
---

### Post by storm99999 on 2008-05-01
Well, I've been trying to find the source of this bug for a while.  What happens is after roughly 30 or so minutes of running, any task will drastically slow down, causing bad lag opening up programs.  A few minutes later, all tasks will only be done after wiggling the mouse, of which the system will perform tasks for a few seconds and stop.  If I continue to work on the computer, after about 2 hours of runtime, the ability to shut down ceases to work and all programs will lock up.

The system can only be shut down by going to a virtual terminal and having root do the job.

For a more specific example, I can be typing in a URL in firefox.  It will cease registering my typing until I move the mouse in which all the characters not previously shown suddenly appear.  When I press enter, the page won't load until I move the mouse again.

Using the uptime command to get load times, it states that my load over the last 1 minute is 7.45, while the only intensive program running is tar (which had ceased working a few minutes ago).

This happened since an update to 7.04 (I think...), and a fresh install (today) of 8.04. The only minor remedy is to build my own kernel (2.6.25 at the time) with low latency desktop mode and a 1000hz clock on the processor.  This only allows some programs to sometimes not be affected. Any idea of what's happening?

---

### Post by storm99999 on 2008-05-04
Any ideas?

Recently, it has been so bad that after a half an hour terminals won't open and Firefox crashes when opened immediately after login.

---

### Post by storm99999 on 2008-05-06
OK, as 2.6.25.1 is out, I was changing settings in the .config, and I came across the scheduler part.  I thought that that might affect it.  When I was researching the different schedulers, I noticed that deadline was recommended for "high performance hard drives".

I found that one could change the scheduler on demand to see what happens.  I started out with CFQ scheduler operational, and forced it to use deadline.  The uptime zeroed out, and the lag went away, so I rebooted with the elevator=deadline boot command.  The system quickly lagged up, so I tried switching back to CFQ.  The lag went away.

So, neither scheduler seems to do anything different, but switching schedulers while running fixes the problem (at least so far).  It's a temporary fix, but I don't much know what to do as I am mostly just learning about the inner workings of Linux, hence the building my own kernel to learn about it's features.  Thank you to anyone who has any idea of what could possibly be going wrong.

---

