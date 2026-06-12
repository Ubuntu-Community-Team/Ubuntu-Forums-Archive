---
title: "Monitor total processing required for job?"
date: 2008-04-23
forum: General Help
---

### Post by Marco_Polo on 2008-04-23
I've been given the task of comparing the performance of two pieces of code (C++), written independently to perform an analysis task.  One of the parameters that I would like to compare is the total processing required by each program.  

I'm running 64-bit hardy on a dell 1420 (probably irrelevant info.)

My only experience monitoring the CPU is with GNOME's "System Monitor."  It shows the usage of each CPU as a function of time, but what I want is to integrate the usage that went into the specific job, for the total processing required (not sure what the units of that are.)

Any ideas?  My only idea is to shut down everything else.  Run one job, measuring the time it takes.  Repeat.  Is that reliable/reproducible?

Thanks for any help.

---

### Post by bingoUV on 2008-04-23
```

time <command>

```

Tells how much computing resources the command required to complete. For more details, see manual page
```

man time

```

---

### Post by Marco_Polo on 2008-04-23
Thanks Bingo!  Another Unix command for the toolbox ...

---

