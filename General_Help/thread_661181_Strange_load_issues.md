---
title: "Strange load issues"
date: 2008-01-07
forum: General Help
---

### Post by eggepegge on 2008-01-07
Hi, I have a newly installed 7.10 on an AMD x64 box running MythTV. For some reason the system load goes up to 1 about every 60-70 minutes although the system is totally idle, and I haven't been able to figure out why this is happening.

One would guess it could be an hourly cronjob, but it isn't as the time it happens is drifting a bit. Another guess is some kind of cleanup job, but I can't see any traces of it whatsoever in the logs or process lists. And there's no iowait when the load increases. Also, it stays around 1 or a bit above for 5 - 10 minutes so one could think it should be easy to spot the culprit. But I just can't :(

If anyone have any ideas, it is more than welcome. Not that it hurts much, but I'd like to know why this is happening. The system is more or less a standard desktop install with the mythtv packages added. It uses the nvidia binary drivers for the graphics card if that makes any difference. And as I said, it is an AMD 64-bit box.

I'm attaching the load graph I'm getting for this box.

Thanks!

---

