---
title: "Time resets to odd values at system startup/wakeup"
date: 2008-02-13
forum: General Help
---

### Post by asaz989 on 2008-02-13
I've been running Ubuntu for a couple of months now, and I've noticed that every couple of times when I reset (or just wake up from hibernate) my system clock is off (usually early) by some round number of hours between 5 and 10.

I can work around this by then going to the time and date settings and manually ordering a synchronization, but in the meanwhile there are issues with things like date modified stamps and the like, with the kernel automatically modifying some because it thinks they were accidentally put 10 hours into the future.

Has anyone seen anything like this before?

---

### Post by seventhc on 2008-02-13
I haven't experienced this before, but I would check the system time in the BIOS.
Make sure that it's correct there.
But as long as your time zone is correct in Ubuntu's settings and your BIOS time is correct, I'm not sure what else it could be.
These are the two things that have effected my system in the past though.

---

