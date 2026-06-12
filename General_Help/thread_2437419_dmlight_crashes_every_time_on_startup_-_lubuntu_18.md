---
title: "dmlight crashes every time on startup - lubuntu 18.04"
date: 2020-02-23
forum: General Help
---

### Post by user99812 on 2020-02-23
I've Googled and read a number of threads but can't find anyone else with this exact problem.  Every time I startup, after logging in, I'll get the classic "System program problem detected" popup.  Looking in /var/crash (see below) seems to suggest it's dmlight crashing.  Anyone know what the issue might be and how to resolve?

> mobile@mobile2:/var/crash$ sudo more _usr_lib_xorg_Xorg.0.crash 
ProblemType: Crash
Architecture: amd64
CrashCounter: 1
Date: Sun Feb 23 19:00:23 2020
DistroRelease: Ubuntu 18.04
ExecutablePath: /usr/lib/xorg/Xorg
ExecutableTimestamp: 1559301048
ProcCmdline: /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
ProcCwd: /
ProcEnviron: PATH=(custom, no user)
ProcMaps:
 563552e3c000-563553080000 r-xp 00000000 b3:01 524390                     /usr/lib/xorg/Xorg
 563553280000-563553284000 r--p 00244000 b3:01 524390                     /usr/lib/xorg/Xorg


---

### Post by andrewbuckle on 2020-03-21
I have exactly the same problem. Same lines in the crash report... 
looking for ideas. Machine is a Dell E4300 laptop with 240GB SSD

---

### Post by wildmanne39 on 2020-03-21
Hello and welcome to the forum andrewbuckle, please start your own thread instead of posting in someone else's because even though the symptoms may be the same many times the cause is different and it gets confusing helping more then one person in the same thread.

---

