---
title: "[SOLVED] Distributed.net slowing downon my PC"
date: 2008-05-16
forum: General Help
---

### Post by steevc on 2008-05-16
I've been running tis distributed processing on my various PCs for several years. Currently I run the OGR project on my Athlon 64 4600 and it was zooming through work. Looking at the log I see that it was managing around 60Mnodes/s, but in the last few weeks it has dropped to around 22. It still uses almost all the time on both cores, so either my processor has slowed down or something about the data being processed has changed.

Any ideas?

---

### Post by Monicker on 2008-05-16
Checked the distributed.net site?  Usually those places will say if something has changed which will cause a difference in client performance.

---

### Post by steevc on 2008-05-16
> **Monicker said:**
> Checked the distributed.net site?  Usually those places will say if something has changed which will cause a difference in client performance.

You obviously don't know them. News trickles out very infrequently. I'm not on the mailing list these days, but there only seems to be a couple of messages each month anyway.

I'm also running it on a Windows PC. That is showing a similar throughput to the Linux box, but is only running in on a single core running slower than each of mine.

I've been running this project on and off since it started and I just thought I would see it through. I'm still contributing, but would like to make sure I am maximising what I process. Not that I am a big fish there. I'm just curious as to what has changed.

---

### Post by steevc on 2008-06-27
It's taken me a while to get around to investigating further. I had a look at /proc/cpuinfo and found that both cores were running at 1GHz instead of 2.4. With a little help from this thread

[http://ubuntuforums.org/showthread.php?t=841368](http://ubuntuforums.org/showthread.php?t=841368)

[EDIT] I've added a note there about changing powernowd settings as a better fix

I found KPowersave that let me set the frequency scaling policy. This is not ideal as I have to set it up for each user. There must be something in a config file that would set it globally.

I'm concerned that something changed this. It may have happened in the last upgrade, but I think it may have been earlier.

I made a further improvement on my dnet scores by setting up a better script for it that shuts it down properly. Otherwise I tended to lose partially done work units. See

[http://faq.distributed.net/cache/84.html](http://faq.distributed.net/cache/84.html)

---

