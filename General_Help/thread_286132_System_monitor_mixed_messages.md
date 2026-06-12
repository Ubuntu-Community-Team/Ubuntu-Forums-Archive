---
title: "System monitor mixed messages"
date: 2006-10-27
forum: General Help
---

### Post by Charles Hand on 2006-10-27
I have kernel 2.6.15-27-686.

Every now and then, system monitor shows that both cpus (core duo) are running at 55%. However, looking in the Processes tab, and sorting by %CPU, there is nothing using more than 3% CPU (system monitor itself).

I have a frequency scaling monitor on my panel which usually shows 1Ghz when things are idle, and during these times when System Monitor Resources shows lots of activity while System Monitor Processes shows little activity, the frequency scaling monitor shows 2GHz.

I have System Monitor Processes page set to show "all processes".

---

### Post by Charles Hand on 2006-10-27
I have kernel 2.6.15-27-686.

Every now and then, system monitor shows that both cpus (core duo) are running at 55%. However, looking in the Processes tab, and sorting by %CPU, there is nothing using more than 3% CPU (system monitor itself). All other processes are using 0%.

I have a frequency scaling monitor on my panel which usually shows 1Ghz when things are idle, and during these times when System Monitor Resources shows lots of activity while System Monitor Processes shows little activity, the frequency scaling monitor shows 2GHz.

I have System Monitor Processes page set to show "all processes".

---

### Post by Charles Hand on 2006-10-27
Interesting. "Top" shows more processes using more than 0% than System Monitor. Still doesn't add up to anything like 50%.

---

### Post by Charles Hand on 2006-10-27
More info:

Shutting down all applications didn't change the amount of CPU usage indicated by system-monitor "resources".

Logging out and logging back in did restore the system to normal. It was not necessary to reboot.

Now I'll keep an eye out to see if one particular application seems to initiate the behavior.

---

### Post by Charles Hand on 2006-10-31
Now it's doing it every time I boot up and before I start any applications. system-monitor says CPU 50%, fan running at high speed, frequency scaling to high as if the computer was doing a lot of work.

Top and system-manager->processes says there's nothing running - maybe 2 or 3% of cpu.

---

