---
title: "Show memory of a single program"
date: 2018-08-07
forum: General Help
---

### Post by raleigh3 on 2018-08-07
I am trying to simply determine how much memory Seamonkey is using.

Is the 782152 bytes the amt. that only Seamonkey is using?

```
andy7_~/Downloads$ top -p 13718

top - 10:59:50 up  2:53,  1 user,  load average: 0.08, 0.12, 0.09
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.3 us,  0.7 sy,  0.0 ni, 98.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  7079816 total,  4343488 free,   782152 used,  1954176 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  5946100 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                             
13718 andy      20   0 2670216 294280  98248 S   0.0  4.2   0:29.11 seamonkey        
```

---

### Post by Holger_Gehrke on 2018-08-07
No, that's the memory used by everything currently running measured in KiB. The memory used by a single program can be found in the column RES. And if you already have the PID of the process, you can get it's resident size with 'ps -o rss= 13718' (using the PID from your post, change as needed ...)

Holger

---

### Post by raleigh3 on 2018-08-07
Thanks.

I know pidof seamonkey will give me the needed pid.

How do I combine that with os -o rss ?

---

### Post by Holger_Gehrke on 2018-08-07
I'd use command line substitution. If you enclose a command in '$()' its output replaces the command in the command line:
```
ps -o rss= $(pidof seamonkey)
```
BTW, pidof will output a list of PIDs if theres mutiple programs of the same name. Further details can be found in the manual pages for ps and pidof. Details on command substitution and a lot of other things can be found in the bash manual page.

Holger

---

### Post by raleigh3 on 2018-08-07
Thanks.

pidof only showed one PID for Seamonkey.

---

