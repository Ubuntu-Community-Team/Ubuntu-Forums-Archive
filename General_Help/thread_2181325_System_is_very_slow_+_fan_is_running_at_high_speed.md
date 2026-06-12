---
title: "System is very slow + fan is running at high speed"
date: 2013-10-17
forum: General Help
---

### Post by Emil_Jung on 2013-10-17
Hi there,
two days ago I decided to remove Windows and install Ubuntu. This is my first time with Linux system for a long time (5 years or something like that). I absolutely love it, everything looks brilliant, just exactly how i would imagine system should be. Must say - they made a big progress. I've got two issues (so far) tho, so hopefully someone will be able to help me. I don't really want to try everything that u can find on the web and messed up.

The first thing I've noticed is that system is working very slow, especially when I'm trying to watch videos on YouTube or something like that. It takes few seconds before any program will open. Even Facebook is loading very slow. I assumed that if my laptop was working perfectly fine on Windows 7 and 8 (even very fast i'd say) everything is gonna be even better on Linux. First thing that came to my mind was wrong graphic card drivers, but I have got no idea how to check if i got the right ones and how to find the ones that suits me best. But probably I'm wrong anyway. 

The other thing is that fan is working extremely fast even if only browser is open. 

And this is my laptops (Sony Vaio) spec:
Processor: 4xIntel Core i3 CPU M380 @ 2.53GHz
Memory: 3gb
Graphic card:
       product: Park [Mobility Radeon HD 5430/5450/5470]
       vendor: Advanced Micro Devices [AMD] nee ATI


And i'm running Ubuntu 13.04. Hope some one can help, I really don't want ot go back to Windows.Thanks.

---

### Post by maslacher on 2013-10-17
Check temperatures. This looks for me like overheating.

---

### Post by Emil_Jung on 2013-10-17
I did. Processor is about 20-25 % only.

---

### Post by VMC on 2013-10-17
From a terminal (Ctrl+Alt+T), run this command, to see which top ten processes are using CPU usage:
```
[COLOR=#333333][FONT=arial]ps axo pcpu,comm,pid,euser | sort -nr | head -n 10[/FONT][/COLOR]
```[COLOR=#333333][FONT=arial]
Its best not to have a browser running, or any other program while you run the test.[/FONT][/COLOR]

---

### Post by Emil_Jung on 2013-10-17
11.5 Xorg             1166 root
 5.4 nautilus         2037 emilsky
 4.8 compiz           2021 emilsky
 2.6 gnome-terminal   8471 emilsky
 0.9 bash             8582 emilsky
 0.6 pulseaudio       1999 emilsky
 0.4 kworker/1:1      8275 root
 0.3 rcu_sched          10 root
 0.2 kworker/0:3      8295 root
 0.2 kworker/0:0      8106 root

---

### Post by Emil_Jung on 2013-10-18
any ideas?

---

