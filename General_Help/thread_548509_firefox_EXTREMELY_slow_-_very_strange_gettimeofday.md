---
title: "firefox EXTREMELY slow - very strange gettimeofday"
date: 2007-09-11
forum: General Help
---

### Post by IndigoMontoya on 2007-09-11
I am having a problem with firefox.  From startup it is running very slow.  Tabs hang, links dont go for some time.  Only when I move away from that window (ie go to another desktop or to another application and come immediately back does the link open.  When I run strace -p pid# on the running firefox I get a large amount of gettimeofday calls when firefox is doing nothing (well I am doing nothing to it).  Is this normal?  This has started recently (ie yesterday it started and today it got bad).

I am running an uptodate fiesty with xgl/compiz

---

### Post by ajgreeny on 2007-09-11
Tried without xgl/compiz running?  It might make a difference.

---

