---
title: "Obitaining per-process filesystem i/o statistics"
date: 2007-03-29
forum: General Help
---

### Post by Xianath on 2007-03-29
Hi all,

I've been looking for a way to check how much I/O a process is, or has been, doing (both deltas and totals are fine - rrdtool can handle both.) When I see one of the CPUs hogged in I/O wait%, I'd like to see which process on that CPU is doing what in terms of I/O. Is there an entry in /proc that would hold this information?

Thank you for your attention,
Peter

---

### Post by jbuberel on 2008-03-11
The capability you are looking for was added into linux kernel version 2.6.20 and later. It is not generally enabled by default. 

Google 'linux iotop' for more information on tools that will allow you to make use of this data.

-jason

---

### Post by Xianath on 2008-05-11
Thanks, I actually found the sysstats package just about a week ago and have been playing with pidstat. I'll definitely give iotop a try in the VM lab.

Cheers,
Peter

---

### Post by markseger on 2008-06-12
This reply is a little old, but I wanted to let people know I've just released a new version collectl - see [http://collectl.sourceforge.net/](http://collectl.sourceforge.net/) which also supports the display of top processes.  However what make collectl different in my opinion is that this is a complete tool which covers most system monitoring needs.  What that means is you can either run a single tool interactively or as a daemon and collect data for later playback instead of having to use multiple ones.  While I do realize there are a lot of tools out there that collect multiple stats I believe most only collect subset of what collectl does, such as infiniband,  quadrics, lustre and more.

In any event, if you want to see what other features make collectl unique, have a look at [http://collectl.sourceforge.net/Features.html](http://collectl.sourceforge.net/Features.html).

-mark

---

