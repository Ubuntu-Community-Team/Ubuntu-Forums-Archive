---
title: "Limewire crashes Ubuntu"
date: 2005-07-28
forum: General Help
---

### Post by dosary on 2005-07-28
I use LimeWire both under Gnome and XFCE. When I turn on LimeWire the machine becomes very slow. If I leave it running it hangs the machine totally and I must press the reset button.
Machine specs: P4, 3GHz, 1GB RAM, 80 GB on LimeWire partition with about 30% free. 
I notice that when it is running, the "wa" in top (IO waiting) is around 90%. I thought that when a CPU is waiting for IO, it should be free for other processes!?
I also notice that the swap space being used is ZERO from the 3.8GB available ... what does that mean?

Here is some stats from my machine before starting LW:
```
top - 15:34:51 up 16 min,  4 users,  load average: 0.23, 0.24, 0.26
Tasks:  70 total,   2 running,  68 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0% us,  1.7% sy,  0.0% ni, 89.4% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1036504k total,   438440k used,   598064k free,    32704k buffers
Swap:  3903784k total,        0k used,  3903784k free,   297304k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6171 root      15   0  152m  21m 6532 S  5.7  2.1   0:11.40 Xorg
 8075 dosary    15   0 98764  34m  17m S  3.3  3.4   0:19.29 firefox-bin
...

dosary@ubi:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 0  0      0 598544  32328 297296    0    0   365    43 1168   551  6  2 81 11

dosary@ubi:~$ free
             total       used       free     shared    buffers     cached
Mem:       1036504     437976     598528          0      32328     297304
-/+ buffers/cache:     108344     928160
Swap:      3903784          0    3903784
```

Here are the same stats one minute after Starting LW:
```
top - 15:41:07 up 23 min,  4 users,  load average: 1.49, 0.57, 0.34
Tasks:  73 total,   1 running,  72 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6% us,  1.2% sy,  0.0% ni,  0.4% id, 88.9% wa,  0.4% hi,  1.6% si
Mem:   1036504k total,   600904k used,   435600k free,    36052k buffers
Swap:  3903784k total,        0k used,  3903784k free,   414732k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8133 dosary    18   0  333m  54m  21m S  6.0  5.4   0:10.43 java
 6171 root      15   0  154m  23m 7052 S  2.0  2.3   0:18.28 Xorg
...

dosary@ubi:~$ vmstat
procs -----------memory---------- ---swap-- -----io---- --system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 4  1      0 448368  35944 405388    0    0   330    34 1179   652  6  2 80 13

dosary@ubi:~$ free
             total       used       free     shared    buffers     cached
Mem:       1036504     591272     445232          0      35948     408460
-/+ buffers/cache:     146864     889640
Swap:      3903784          0    3903784
```

Does anyone have an idea what the problem might be?

TIA

---

### Post by theturner on 2005-07-28
Well, you've still got a lot of RAM free, so don't worry about the swap. 

The problem is most probably that Java sucks. What JRE version are you using?

---

