---
title: "mysterious IO wait"
date: 2012-11-19
forum: General Help
---

### Post by ghat on 2012-11-19
hi
I have this mysterious IO Wait
```

top - 04:03:50 up 5 min,  3 users,  load average: 1.66, 1.42, 0.73
Tasks: 199 total,   1 running, 198 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  1.2%sy,  0.0%ni, 57.4%id, 40.8%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   8046940k total,  1577936k used,  6469004k free,   182568k buffers
Swap: 11653116k total,        0k used, 11653116k free,   485928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                               
  250 root      20   0     0    0    0 S    1  0.0   0:01.60 jbd2/dm-1-8                            
 1388 root      20   0  426m 202m  37m S    1  2.6   0:23.73 Xorg                                   
    3 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/0                            
    4 root      20   0     0    0    0 S    0  0.0   0:00.07 kworker/0:0                            
   55 root      20   0     0    0    0 S    0  0.0   0:00.38 kworker/u:8                            
  122 root      20   0     0    0    0 S    0  0.0   0:00.64 kworker/1:2                            

```

Can anyone guide me as to how I go about figuring it out ?
I have no zombie process' the above top is after a fresh reboot

G
PS: Ubuntu 12.04.1/ amd64 using 
Linux desktop 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Doug S on 2012-11-19
An [interesting article ]("http://www.chileoffshore.com/en/interesting-articles/126-linux-wait-io-problem")that might help.

---

### Post by rnerwein on 2012-11-19
> **ghat said:**
> hi
I have this mysterious IO Wait
```

top - 04:03:50 up 5 min,  3 users,  load average: 1.66, 1.42, 0.73
Tasks: 199 total,   1 running, 198 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  1.2%sy,  0.0%ni, 57.4%id, 40.8%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   8046940k total,  1577936k used,  6469004k free,   182568k buffers
Swap: 11653116k total,        0k used, 11653116k free,   485928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                               
  250 root      20   0     0    0    0 S    1  0.0   0:01.60 jbd2/dm-1-8                            
 1388 root      20   0  426m 202m  37m S    1  2.6   0:23.73 Xorg                                   
    3 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/0                            
    4 root      20   0     0    0    0 S    0  0.0   0:00.07 kworker/0:0                            
   55 root      20   0     0    0    0 S    0  0.0   0:00.38 kworker/u:8                            
  122 root      20   0     0    0    0 S    0  0.0   0:00.64 kworker/1:2                            

```Can anyone guide me as to how I go about figuring it out ?
I have no zombie process' the above top is after a fresh reboot

G
PS: Ubuntu 12.04.1/ amd64 using 
Linux desktop 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

hello
i can tell you -->the most reason for high WIO arise in programmerland and userland...
as an example: you have running a big server with 1000 of tasks and there applications where all of them store tempory date in a single directory then you will have a high wait-io ( on disk or in the dnls lookup cache).
post a complete output of your running system using the command: ps -elf
to see where your tasks hanging around ( with ps -elf you can see the WCHAN)
so long

---

