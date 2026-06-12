---
title: "Ubuntu 6.10 Edgy Server System is lagging!"
date: 2007-09-10
forum: General Help
---

### Post by barisy on 2007-09-10
:confused:Hello everyone;
We have using 6.10 fiesty server, working firewall on it, 1Gig RAM, 160GB HDD and having problems with this server, the system is lagging all the time, is there any way to monitor the leakage or malfunction whatever in order to understand whats happening to this machine? I tried "top" but did not see any clue that tells me where the abnormality is?! Please tell me what would be the possibilities? Thank you and have a nice day!

---

### Post by strider1551 on 2007-09-10
Check out [this thread]("http://ubuntuforums.org/showthread.php?t=546566") from the other day.  It should give you a place to start looking.

Other than that, use basic problem solving.  Is your ram usage unreasonably high?  If so, what programs are using a significant amount of ram?  If not, what else could cause the lag that you are experiencing?

As a general rule, always try to narrow down the possibilities.  It will make finding the solution easier.

---

### Post by barisy on 2007-09-10
Thank you for the redirection, i'll try the possibilities.

BTW the top is like this compared to the other pal's "top" this "top" is more confusing actually since;

```
top - 04:11:58 up  6:02,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  65 total,   1 running,  64 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035376k total,   133284k used,   902092k free,    70880k buffers
Swap:  1951856k total,        0k used,  1951856k free,    31460k cached

```

nothing happening considerable on this system and no processes forcing at all ..

this is top 10

```
    1 root      17   0  1632  536  448 S    0  0.1   0:01.13 init                                                                                                                  
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                           
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                                           
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                            
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                           
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                                           
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                            
    8 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                                              
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                                              
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                               
```
anyway thanks for the help.

---

