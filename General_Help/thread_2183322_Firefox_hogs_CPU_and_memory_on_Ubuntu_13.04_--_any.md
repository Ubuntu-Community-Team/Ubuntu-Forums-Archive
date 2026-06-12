---
title: "Firefox hogs CPU and memory on Ubuntu 13.04 -- any known fixes?"
date: 2013-10-24
forum: General Help
---

### Post by le_jawa on 2013-10-24
All,

I've been running 64-bit Ubuntu 13.04 in a desktop VM for a few months now and have been loving it, overall.  However, I've had a re-occurring problem that's been driving me nuts, and I haven't found a solution for it.  Firefox has tendancy to chew up tons of memory and CPU time; pages with Flash seem to be the main offenders.  In particular, our company's Jira system kills it.  Whenever a flash animation runs (such as when a Jira page is being refreshed) Firefox pegs both CPUs allocated to the VM and freezes until it finishes doing whatever it's doing, then gives the CPU a break and runs right again.

Also, under heavy usage it will hog memory to the point that I finally have to exit it, empty the swap file, and restart the browser.

Granted, having 10-15 tabs open in a browser takes up a lot of memory, but where Firefox will consume about 1.5GB or so itself, using Chrome keeps the memory used by the browser down to around 700MB - 1GB.  And it never pegs the CPU, even in Jira.

Is this an issue with the 64-bit Ubuntu Firefox build? (I haven't seen anything like this on the Windows build.)  If so, has it been resolved in 13.10?  Or is it something with the Flash player and Firefox's plugin-container?   (I'm  using the actual Adobe flash player, not an open-source alternative).  If anyone as any useful info on this issue, I'd love to hear it.

Thank you,

Jason

---

