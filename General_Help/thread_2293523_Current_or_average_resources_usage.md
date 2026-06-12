---
title: "Current or average resources usage?"
date: 2015-09-05
forum: General Help
---

### Post by Dmitry_Samokhin_Ic on 2015-09-05
Hey guys, i need a little help. Long story short is that im making control panel for my game servers and i want to display resources usage.
At the moment i have these command: (samp03svr being file and process name)
```
ps -C samp03svr -o %cpu,%mem,cmd
```
Returned info is:
```
%CPU %MEM CMD 
0.8  1.7 ./samp03svr
```
Now is these current or average usage? Also CPU is at 0.8, but what is a maximum? (if im right there should be command to check and/or setup these param..)
Also if these is average usage, how do i get current, or vice versa.

Sorry for stupid questions and thanks in advance.

---

### Post by Dmitry_Samokhin_Ic on 2015-09-06
bump

---

### Post by Doug S on 2015-09-06
From the man page for ps (and verified by experiment):```
       %cpu        %CPU      cpu utilization of the process in "##.#" format.  Currently, it is the CPU time used divided by the time the process has been running (cputime/realtime ratio),
                             expressed as a percentage.  It will not add up to 100% unless you are lucky.  (alias pcpu).
```
For memory use (again, verified by experiment), it is the percentage used by the program at the time of execution of the ps command.

---

