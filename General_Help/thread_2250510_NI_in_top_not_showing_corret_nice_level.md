---
title: "NI in top not showing corret nice level"
date: 2014-10-29
forum: General Help
---

### Post by geohei on 2014-10-29
Hi.

I started testtask twice. Both times with nice -10. However the NI column in top doesn't show correct nice level. The first time it shows -1 and the second task shows 10.

How come?

Both should show -10, right?

```
root@gan:~# top -p 18599,18601
top - 09:09:00 up  1:20,  1 user,  load average: 0.09, 0.12, 0.13
Tasks:   2 total,   0 running,   2 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.4%us,  0.5%sy,  0.1%ni, 98.6%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7744416k total,  1773728k used,  5970688k free,    72652k buffers
Swap:  3906556k total,        0k used,  3906556k free,   465496k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
18599 root      19  -1 36656 2592 1316 S    2  0.0   0:02.33 testtask
18601 root      30  10 16432 4548 1324 S    1  0.1   0:00.81 testtask
```

---

### Post by geohei on 2014-10-30
Ok ... mistake from my side. I "forgot" the -n with the nice command.

Here now the script which starts both tasks:

```
...
nice -n -5 /usr/bin/testtask -b
nice -n -5 /usr/bin/testtask -b
...
```

But the result is that only 1 task is -5 and the other one -1.

```
root@gan:~# top -p 1650,1652
Tasks:   2 total,   0 running,   2 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  0.4%sy,  0.0%ni, 98.5%id,  0.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7744416k total,   831568k used,  6912848k free,    67808k buffers
Swap:  3906556k total,        0k used,  3906556k free,   215328k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1650 root      19  -1 37620 3636 1508 S    4  0.0   1:33.43 testtask
 1652 root      15  -5 16504 5596 1536 S    1  0.1   0:15.63 testtask
```
How come?

---

### Post by geohei on 2014-10-31
I noticed that testtask starts 2 tasks:
```
root@gan:~# ps -e -o uid,pid,ppid,pri,ni,cmd | grep oscam
    0  1639     1  24  -5 /usr/bin/testtask
    0  1641  1639  20  -1 /usr/bin/testtask
    0  1642     1  24  -5 /usr/bin/testtask
    0  1643  1642  24  -5 /usr/bin/testtask
```
Ok ... this is quite common, but why is one child task -1 (1641) while the other one is -5 (pid 1643)?
Does the child task no inherit the nice level of the parent task?
For parent pid 1642, this works, but not for parent pid 1939.
Why?

---

### Post by geohei on 2014-11-04
I found the source of the problem.

NI -1 for PID 1641 was set by a configuration line, which lets the user define the nice level without using the nice command upon start of the testtask binary.

After removing this line, all NIs went to -5 as expected.

---

