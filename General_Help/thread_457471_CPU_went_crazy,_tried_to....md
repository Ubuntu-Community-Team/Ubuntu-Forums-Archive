---
title: "CPU went crazy, tried to..."
date: 2007-05-28
forum: General Help
---

### Post by Eric the Red on 2007-05-28
I was on my computer when I noticed my CPU went up to 100% so I thought that it was kind of suspicious and ran the command "top" to see the processes and their CPU utilization. the name of the process that was taking 100% CPU was called "loop()". Is there anymore commands that I can use to find out exactly where this process started from? 

Any help would be greatly appreciated.

---

### Post by Jussi Kukkonen on 2007-05-28
ps is a good start. Try a process tree:
```
ps -ejH
```
It'll show if another process owns the loop process. *ps ax* will show you the whole command that was used (with path).

---

