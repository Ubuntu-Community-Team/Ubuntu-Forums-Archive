---
title: "What is top trying to say?"
date: 2005-10-30
forum: General Help
---

### Post by dgs on 2005-10-30
Hi there,

I need help interpreting my top output below. My computer runs terribly slow sometimes (can't tell you exactly when... it happens now and then) and now I wonder if someone could help me to solve this issue.

I got a ~2 GHz athlon and runs it with a own-compiled kernel (I tried the shipped k7-kernel aswell).

I guess it's strange that dc++ (not connected - nothing in queue) takes up 64 % cpu for several minutes making mycomputer almost unusable and later it stabilizes at ~7 percent... The physical mem is full and swap is empty... why is this?

It feels like running a Micro$oft os when my computer suddenly decides to think for itself for a few minutes beyound my control... 

> top - 13:57:34 up  1:11,  2 users,  load average: 1.99, 2.29, 2.10
Tasks:  73 total,   2 running,  71 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.1% us, 17.5% sy, 33.7% ni,  0.0% id, 23.8% wa,  3.3% hi,  0.7% si
Mem:    906608k total,   898140k used,     8468k free,      968k buffers
Swap:  2040212k total,        0k used,  2040212k free,   629020k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 9054 dennis    15   0  143m  44m  10m S 64.1  5.0   4:32.97 dcpp
 6990 root      16   0  138m  65m 9880 R  7.9  7.4   5:26.06 Xorg
   91 root      15   0     0    0    0 S  1.3  0.0   0:43.91 kswapd0
 9189 dennis    15   0 32136  13m 8872 S  0.7  1.5   0:02.27 gnome-terminal
 7017 cupsys    16   0  6284 3332 1260 S  0.3  0.4   0:01.91 cupsd
    1 root      16   0  1564  492  432 S  0.0  0.1   0:01.09 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.34 events/0
    4 root      13  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   61 root      10  -5     0    0    0 S  0.0  0.0   0:01.26 kblockd/0
   89 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
   90 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush
   92 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  677 root      19   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1917 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 3116 root      15   0     0    0    0 S  0.0  0.0   0:00.14 kjournald
 3262 root      15  -4  1660  548  460 S  0.0  0.1   0:00.19 udevd
 6117 root      16   0  2328 1116  820 S  0.0  0.1   0:00.00 dhclient3
 6465 root      16   0  1824  992  532 S  0.0  0.1   0:00.00 acpid
 6480 syslog    16   0  1760  752  632 S  0.0  0.1   0:00.01 syslogd
 6497 root      15   0  1560  364  300 S  0.0  0.0   0:00.02 dd


Regards, 
Dennis

---

### Post by frenkel on 2005-10-30
It's checksumming your files when it uses that much CPU. And don't whine about the memory, Linux just likes to cache stuff, because empty memory is useless memory. When you're really out of memory, apps will get killed and you'll get error messages about it. Now it's just caching stuff in memory, and that's a Good Thing.

---

