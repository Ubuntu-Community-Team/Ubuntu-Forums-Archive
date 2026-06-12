---
title: "Why would Ubuntu not boot until I turned off other computers?"
date: 2021-10-06
forum: General Help
---

### Post by Old Jimma on 2021-10-06
Hello Community:

I updated and tried to restart my main Ubuntu computer this morning.

... And it would not restart.

There are 2 other Ubuntu computers that "communicate" with my main Ubuntu computer:
[LIST=1]
[*]a laptop that shares files with my main computer via nfs, and
[*]a raspberry pi that communicates with my main computer via ssh... to pull data from my main Ubuntu computer to archive the main Ubuntu computer's file system every 4 days using rsync.
[*]
[/LIST]

I did  a little digging and learned that one plausible reason why my main Ubuntu computer would not boot was because other file systems mounted to my main computer.

I did not understand this fully, but when I turned the laptop an pi off, my main computer booted nicely.

**What should I do to avoid this problem in the future?**

Thanks,
Old J

---

### Post by HermanAB on 2021-10-07
Maybe you just have an IP Address clash?

---

