---
title: "firefox randomly closes"
date: 2007-12-23
forum: General Help
---

### Post by libertas on 2007-12-23
Firefox randomly closes on me no patten at all just closes for no apparent reasonr, I have seen other threads with this problem but none of them have brought up firefox in the terminal and checked to see what the problem was (I did) this is what it said
eric@eric-laptop:~$ firefox

Segmentation fault (core dumped)

eric@eric-laptop:~$
could someone please respond to this, its a rather irritating problem

---

### Post by jago25_98 on 2007-12-24
your pleas for help need to indicate more effort; aids people helping.

you'll need firefox version info, plugins

but before you bother with all that stuff:

1) remove all plugins for testing
2) upgrade if possible, if not consider downgrade firefox
3) put plugins back, only the ones you actually use

that'll do for my charity today methinks

oh step 4 could be analyse core dump (no thanks) or,
try swiftfox and step 5 could be, try epiphany

- random guy

---

### Post by rechick on 2007-12-24
Segmentation faults are related to memory writes by the program. This can be caused by a number of possibilitys (1) bad memory area (2) poorly written code (3) another program inaccrately tagging memory as avaialble which is read only. Tracking it down is a long process which often has no concrete results. If you have more than one Memory DIM in your computer the first place to start is swapping their positions to see if it relieves the situation. Looking at the core dump, if you have the time and epertise, can also reveal the location of the fault. 

Not much help but hopefully gives an indication of what you're trying to resolve.

---

### Post by libertas on 2008-03-11
removed some plugins and that seemed to be the problem, good ideas guys!

---

