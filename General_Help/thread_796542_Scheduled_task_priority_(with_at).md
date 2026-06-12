---
title: "Scheduled task priority (with at)"
date: 2008-05-16
forum: General Help
---

### Post by Jonie on 2008-05-16
When you run a program as a user it's given nice value of 0. The same task run by at is given nice +2 and since normal user may not renice his tasks to a higher priority this means highest priority for at scheduled tasks is +2.

Of course you can schedule task by sudo to obtain full control over it and renice the task to higher priority . But one can anyway renice the task to a lower priority as normal user, so what's the point of limiting at-scheduled tasks to +2? So that they don't interfere with foreground programs?

I found this troublesome cause with my setup, all optimizations, deinterlacing, mencoder (an "at" VCR) works unstable with nice value of 2.

So to sum it up - is it a general limit or is it Ubuntu / Debian specific feature?

---

