---
title: "huge delay in application launch"
date: 2007-03-22
forum: General Help
---

### Post by _Jacky_ on 2007-03-22
Hi all,

I have started having huge problems with a handful of applications, namely SPE (Stani's Python Editor), Bibus and cups so far, in that they will only start up with a very big delay (about 20 mins..).

I reckon this is somewhat due to unresponsiveness of gnome since the processes are running but seem to be lost somewhere in the background. Also, once the application is finally there it is very very slow.

Does anyone have an idea what this could be / had similar problems? I am totally lost on that one and really can't establish a connection between the apps that aren't working.

Help would be much appreciated :)

Jacky

---

### Post by benteveo on 2007-03-26
Teach a man how to fish....

Go to a terminal, and start the slow apps under strace. e.g. 

   ```
 $ strace program_name args...
```

This should show you what are the system calls that take so long to complete (i.e. where the application is stuck).

Common causes I've seen in the past may be misconfiguration of dynamic library paths, or network operations (e.g. DNS lookups)  that block and fail.

The next step after figuring out the cause, is to fix what's broken, but we have to figure out what's broken first.  Good luck.

---

