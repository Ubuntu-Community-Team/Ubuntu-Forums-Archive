---
title: "xinit program segfault"
date: 2007-10-30
forum: General Help
---

### Post by bdk6m2007 on 2007-10-30
I'm having a weird problem that started with my recent upgrade to gutsy.  Under fiesty, I was starting an application in rc.local just fine.  Under gutsy when I start the application from the command line (using the same xinit command that's in rc.local) it works just fine.  When I put it in rc.local, however, the process just disappears.
 
I don't see any logs anywhere that indicate what happened to the program.  I modified the command slightly to use strace and found that my program is now seg faulting.  Although I won't rule it out, it seems very likely that my program is OK.
 
Does anyone have any ideas on what could be going wrong here?

---

