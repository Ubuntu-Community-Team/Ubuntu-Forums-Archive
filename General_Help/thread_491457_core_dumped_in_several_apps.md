---
title: "core dumped in several apps"
date: 2007-07-03
forum: General Help
---

### Post by cowkiller on 2007-07-03
Hi people...

I'm having this problem lately... almost every program crashes and exits at any moment just because. The only message I can get running them from a console is "segmentation fault (core dumped)"

Lately it's been happening a lot, wich is so annoying... any Idea of what to do?¿

Thanks in advance!

---

### Post by badtlc on 2007-07-03
I have the same problem with gsopcast.

---

### Post by pjkoczan on 2007-07-03
My best guess, and this is admittedly a stab in the dark, is virtual memory corruption. Something got swapped in/out when it shouldn't have been and now things are just plain messed up. It's also likely a race condition (to those not in the know, a race condition is a timing-dependent bug caused by two or more processes trying to access or modify the same resource at once and not waiting on the other to finish nicely...they are very hard to detect, debug, and replicate). If a lot of programs were running at once when you noticed this, it would point to a race condition.

I have a question for you: does this problem persist after a reboot? If it goes away, then your core dumps are the result of something volatile (memory, for instance).

If possible, you could try using gdb or valgrind to debug the programs, but I don't even know if you'd be able to install or use them given the constant core dumps for, as you say, almost every program.

If you can be very detailed about the conditions that caused your machine to get in this state, you might want to file a bug report.

---

