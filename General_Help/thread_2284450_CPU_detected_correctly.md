---
title: "CPU detected correctly?"
date: 2015-06-29
forum: General Help
---

### Post by xWEkxhW on 2015-06-29
Hello,

Can you confirm the CPU is being detected correctly? It's showing 1 thread per core - does that mean 1 physical and 1 virtual core? i.e. a total of 8 cores, 4 physical, 4 virtual. /proc/cpuinfo shows only 4 cores, but I assume this is only showing physical cores?

Thanks very much

```
$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 60
Model name:            Intel(R) Core(TM) i5-4430 CPU @ 3.00GHz
Stepping:              3
CPU MHz:               2854.804
CPU max MHz:           3200.0000
CPU min MHz:           800.0000
BogoMIPS:              5998.76
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              6144K
NUMA node0 CPU(s):     0-3

```

---

### Post by v3.xx on 2015-06-29
Threads are something else.

[https://en.wikipedia.org/wiki/Thread_%28computing%29](https://en.wikipedia.org/wiki/Thread_%28computing%29)

Looks like an i5 has a single thread per core and an i7 has 2 per core, making it faster.

---

### Post by v3.xx on 2015-06-29
You do not have hyper-threading
[http://ark.intel.com/products/75036/Intel-Core-i5-4430-Processor-6M-Cache-up-to-3_20-GHz](http://ark.intel.com/products/75036/Intel-Core-i5-4430-Processor-6M-Cache-up-to-3_20-GHz)

---

### Post by xWEkxhW on 2015-06-29
You're right, I didn't spot that. Not a problem, just out of interest :-)

Thanks very much

---

### Post by v3.xx on 2015-06-29
That is not a high end 4 core, but not a low end either.  Your 4 core should be fast with any linux you run.

I had one old 4 core that ran at something like 0.8MHz (AMD); first thing I noticed was how fast it was.  You have plenty of horse power :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by xWEkxhW on 2015-06-29
Yep, horsepower is not a problem. It's very powerful and more than enough for what I use the server for. It's a lovely CPU, very happy with it.

I bought it a few years ago because it was a low power variant, doesn't produce too much heat, and so on.

I have no complaints  :-)

---

