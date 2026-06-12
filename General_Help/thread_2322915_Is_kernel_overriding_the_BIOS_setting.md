---
title: "Is kernel overriding the BIOS setting?"
date: 2016-05-01
forum: General Help
---

### Post by bswarm2 on 2016-05-01
Question... When I was running Ubuntu 14.04, I was getting freeze-ups with kernel 3.x, and even more with kernel 4.2. I set the bios to max cstate=1 and that fixed the problem. I installed Ubuntu 16.04 LTS with kernel 4.4 and left the bios setting alone, but "cat /sys/module/intel_idle/parameters/max_cstate" says "9". Is the kernel overriding the bios setting? I've read that some kernels will override the bios for max cstate. It's not freezing up or anything. In fact, this is the fastest and most stable version (so far) of Ubuntu I've used since 10.04.
Edit: My post was moved to it's own thread, this is related to the Bay Trail freeze up problem described [here]("http://ubuntuforums.org/showthread.php?t=2314964") and [here]("https://bugzilla.kernel.org/show_bug.cgi?id=109051").

---

