---
title: "Socket keeps running"
date: 2007-11-09
forum: General Help
---

### Post by chjustc on 2007-11-09
Hi there,

I am using Kubuntu 7.04 on a dell desktop.  Recently, I noticed that the command socket keeps running for very long time and is using all the CPU time.  I tried to stop it by kill -9.  But, it will start to do this again later.  My guess is that socket is trying to reach some device with some difficulty.  Is there any way that I can look into what the socket is doing  here.  

The following is the output I have when I run the command top.  You can see that socket has been running for a long time and is taking all the CPU time.

top - 16:38:45 up 3 days,  5:06,  1 user,  load average: 1.73, 1.49, 1.40
Tasks: 119 total,   4 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us, 39.0%sy,  5.2%ni, 49.4%id,  0.0%wa,  0.0%hi,  5.2%si,  0.0%st
Mem:   1034196k total,  1017516k used,    16680k free,    42220k buffers
Swap:  1534168k total,    33856k used,  1500312k free,   515916k cached

  PID    USER      PR  NI  VIRT    RES  SHR S %CPU %MEM    TIME+      COMMAND
11477 cupsys    35  10  3320  900  720  R  102     0.1      306:24.75  socket
 4843 root      15   0  272m  73m 6248 R    3  7.3   7:59.93 Xorg
    1 root      15   0  2908 1848  524 S    0  0.2   0:01.49 init
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0

Thanks!

---

