---
title: "ubuntu not going to sleep"
date: 2014-04-03
forum: General Help
---

### Post by Chuck_Finley on 2014-04-03
in power options I have my settings to suspend after one hour of inactivity. It never does. Is suspend the same as sleep?

---

### Post by rbmorse on 2014-04-03
I don't know if suspend == sleep, but I've found if i have any chron jobs running as root my machine will not suspend.  Killing those jobs, or setting them up as user-level tasks, allows suspend to function normally. The problem is that user-level chron jobs don't happen if the machine is supended when the designated start time rolls around...or at least I haven't figured out how to get them to wake the machine to run.

---

