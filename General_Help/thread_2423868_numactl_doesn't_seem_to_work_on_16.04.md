---
title: "numactl doesn't seem to work on 16.04"
date: 2019-07-30
forum: General Help
---

### Post by michaeltree on 2019-07-30
I am running a CUDA application on a server with Nvidia T4 GPU. My OS is Ubuntu 16.04.4 LTS with kernel 4.4.0-116. When I use numactl command to specify which numa node to use, my application process is always pinned to CPU core 0 (see details below). I tested both CPU binding and node binding. Any help?

Hardware: Dell R740, [COLOR=#172B4D][FONT=-apple-system]Intel Xeon Silver 4114 CPU, 2 * 10 cores. 

[/FONT][/COLOR]```
[FONT=&amp]$ numactl -H[/FONT]
[FONT=&amp]available: 2 nodes (0-1)[/FONT]
[FONT=&amp]node 0 cpus: 0 2 4 6 8 10 12 14 16 18[/FONT]
[FONT=&amp]node 0 size: 95110 MB[/FONT]
[FONT=&amp]node 0 free: 92794 MB[/FONT]
[FONT=&amp]node 1 cpus: 1 3 5 7 9 11 13 15 17 19[/FONT]
[FONT=&amp]node 1 size: 96735 MB[/FONT]
[FONT=&amp]node 1 free: 95662 MB[/FONT]
[FONT=&amp]node distances:[/FONT]
[FONT=&amp]node   0   1 [/FONT]
[FONT=&amp]  0:  10  21 [/FONT]
[FONT=&amp]  1:  21  10 [/FONT]

```
I used top to view the per-core utilization

```
[FONT=&amp]top - 13:30:50 up  2:20,  3 users,  load average: 0.11, 0.12, 0.16[/FONT]
[FONT=&amp]Tasks:** 324 **total,**   2 **running,** 322 **sleeping,**   0 **stopped,**   0 **zombie[/FONT]
[FONT=&amp]%Cpu0  :** 77.2 **us,** 22.4 **sy,**  0.0 **ni,**  0.3 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu1  :**  0.0 **us,**  0.3 **sy,**  0.0 **ni,** 99.7 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu2  :**  0.0 **us,**  0.3 **sy,**  0.0 **ni,** 99.7 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu3  :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu4  :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu5  :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu6  :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu7  :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu8  :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu9  :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu10 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu11 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu12 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu13 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu14 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu15 :**  0.0 **us,**  0.3 **sy,**  0.0 **ni,** 99.7 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu16 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu17 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu18 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]%Cpu19 :**  0.0 **us,**  0.0 **sy,**  0.0 **ni,**100.0 **id,**  0.0 **wa,**  0.0 **hi,**  0.0 **si,**  0.0 **st[/FONT]
[FONT=&amp]KiB Mem :** 19645052+**total,** 19252579+**free,**  1374988 **used,**  2549736 **buff/cache[/FONT]
[FONT=&amp]KiB Swap:**   998396 **total,**   998396 **free,**        0 **used.** 19419211+**avail Mem[/FONT]
```

---

