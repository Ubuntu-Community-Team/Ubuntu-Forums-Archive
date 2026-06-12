---
title: "Kernel panic on cold boot at the start of the day."
date: 2005-09-03
forum: General Help
---

### Post by Mustard on 2005-09-03
Just lately I have noticed that Ubuntu is hanging on startup with a Kernel panic error.  I can reset and it loads  up Ubuntu just fine (most times), but the first boot of the day is always failing.  How would you diagnose this problem?

---

### Post by d1337 on 2005-09-03
It's been my experience that initial boot issues are sometimes related to the physical condition of the machine...connections, dirt/dust and the like.  Just a thought.  Is this a dual boot?  If so, are you  having issues in the other OS?  I had sporadic kernel panic issues on a box at work recently that I seem to have remedied by making some adjustments in bios.  Since this doesn't always happen, have a look at dmesg for any funky errors that might give more info for a diagnosis.

d1337

---

