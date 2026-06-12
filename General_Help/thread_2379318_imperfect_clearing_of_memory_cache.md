---
title: "imperfect clearing of memory cache"
date: 2017-12-04
forum: General Help
---

### Post by mirzman on 2017-12-04
Hi all, 

I'm getting memory leaks and I can't stop it. "free" utility says it's buff/cache.

```
root@mirzman-workstation:~# uname -a
Linux mirzman-workstation 4.4.0-101-generic #124-Ubuntu SMP Fri Nov 10 18:29:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

root@mirzman-workstation:~# uptime
 13:16:43 up 1 day,  1:48,  1 user,  load average: 1,99, 1,55, 1,31

root@mirzman-workstation:~# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:       16294632     3565680     8753136      637520     3975816    10234368
Swap:      16636924           0    16636924
              total        used        free      shared  buff/cache   available
Mem:       16294632     3562432    10137124      628476     2595076    10311932
Swap:      16636924           0    16636924

...

root@mirzman-workstation:~# uptime
 12:44:58 up 4 days,  1:16,  1 user,  load average: 1,31, 1,15, 0,91

root@mirzman-workstation:~# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:       16294632     2906596     4779968      703336     8608068     6714308
Swap:      16636924           0    16636924
              total        used        free      shared  buff/cache   available
Mem:       16294632     2904376     6590888      696004     6799368     6789688
Swap:      16636924           0    16636924

```

This started several months ago. Maybe I'm doing something wrong?

Thanks ahead.

---

### Post by The Cog on 2017-12-04
That's not a problem, it's a feature.
buff/cache is memory being used for disk caching. Whenever you read from disk, the OS caches the data in case you want to read it again. It makes things faster. If a running program ever wanted more memory than was truly free, the OS would reallocate some of that cache memory, so the program would not go without. It's just making se of memory that would otherwise be truly wasted.

Here's an old page describing the issue: [https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

---

### Post by mirzman on 2017-12-04
> the OS would reallocate some of that cache memory
But this don't happen :( After several days system goes to swap

---

### Post by Doug S on 2017-12-05
Does using top, and sorting by memory use, provide any insight? Similar information can be obtained using ps.

Examples:

```
# ps --sort -rss -eo pid,pmem,rss,vsz,comm | head -20
  PID %MEM   RSS    VSZ COMMAND
 1349  4.8 147792 1312696 mysqld
 1250  1.5 47208 311488 named
17557  0.8 25884 250096 apache2
 8237  0.4 12504 346112 smbd
 1261  0.3 10984  35784 dhcpd
18630  0.3 10940 250552 apache2
18509  0.3 10936 250616 apache2
19287  0.3 10920 250616 apache2
19291  0.3 10876 250552 apache2
20123  0.3 10876 250552 apache2
19299  0.3 10872 250552 apache2
19296  0.3 10856 250552 apache2
19298  0.3 10844 250552 apache2
25547  0.3 10828 250552 apache2
24435  0.3 10800 250536 apache2
 1123  0.2  6596 338328 smbd
 9236  0.2  6452  95404 sshd
 1370  0.2  6372 287672 winbindd
 1367  0.2  6268 287276 winbindd
```
```
top - 10:33:46 up 13 days, 21:41,  6 users,  load average: 0.00, 0.00, 0.00
Tasks: 140 total,   1 running, 139 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.2 us,  0.0 sy,  0.0 ni, 99.3 id,  0.5 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3070448 total,  2629464 free,   304796 used,   136188 buff/cache
KiB Swap:  3133436 total,  3131072 free,     2364 used.  2587380 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1349 mysql     20   0 1312696 147792   3832 S   0.0  4.8   6:27.00 mysqld
 1250 bind      20   0  311488  47208   2640 S   0.0  1.5   3:14.20 named
17557 root      20   0  250096  25884  18548 S   0.0  0.8   0:13.52 apache2
 8237 root      20   0  346112  12504   8708 S   0.0  0.4   1:49.15 smbd
 1261 dhcpd     20   0   35784  10984   1340 S   0.0  0.4   0:00.89 dhcpd
18630 www-data  20   0  250552  10940   3216 S   0.0  0.4   0:00.05 apache2
18509 www-data  20   0  250616  10936   3216 S   0.0  0.4   0:00.04 apache2
19287 www-data  20   0  250616  10924   3216 S   0.0  0.4   0:00.04 apache2
19291 www-data  20   0  250552  10876   3216 S   0.0  0.4   0:00.04 apache2
20123 www-data  20   0  250552  10876   3216 S   0.0  0.4   0:00.02 apache2
19299 www-data  20   0  250552  10872   3216 S   0.0  0.4   0:00.04 apache2
19296 www-data  20   0  250552  10856   3216 S   0.0  0.4   0:00.04 apache2
19298 www-data  20   0  250552  10844   3216 S   0.0  0.4   0:00.04 apache2
25547 www-data  20   0  250552  10828   3216 S   0.0  0.4   0:00.00 apache2
24435 www-data  20   0  250536  10800   3216 S   0.0  0.4   0:00.00 apache2
 1123 root      20   0  338328   6596   4028 S   0.0  0.2   0:05.44 smbd
 9236 root      20   0   95404   6452   5512 S   0.0  0.2   0:01.63 sshd
 1370 root      20   0  287672   6372   4224 S   0.0  0.2   0:10.71 winbindd
 1367 root      20   0  287276   6268   4136 S   0.0  0.2   0:08.36 winbindd

```

---

### Post by mirzman on 2017-12-06
```
root@mirzman-workstation:~# uptime
 12:17:55 up 6 days, 49 min,  1 user,  load average: 1,53, 1,16, 1,06

root@mirzman-workstation:~# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:       16294632     5716904      521056      679032    10056672     1186232
Swap:      16636924      128064    16508860
              total        used        free      shared  buff/cache   available
Mem:       16294632     5722856     1250152      659056     9321624     1251884
Swap:      16636924      128064    16508860
```

It's already use swap! But in the same time buff/cache=9321624

> Does using top, and sorting by memory use, provide any insight? Similar information can be obtained using ps.

It's browser. But restarting of browser won't fix problem. Several days later system goes to swap in any way.
Maybe disabling of swap will make buff/cache to work correctly?

```
root@mirzman-workstation:~# ps --sort -rss -eo pid,pmem,rss,vsz,comm | awk '{sum+=$3}END{print sum}'
7088432

root@mirzman-workstation:~# ps --sort -rss -eo pid,pmem,rss,vsz,comm | head -20
  PID %MEM   RSS    VSZ COMMAND
 7392  5.7 939048 2968784 Web Content
 7164  4.4 720768 3052668 Web Content
 7121  4.3 713492 2926076 Web Content
 6993  4.0 657660 9349752 firefox
 7350  3.5 581168 2641452 Web Content
 1827  3.2 533556 1956640 compiz
 2095  2.6 424004 2976600 Telegram
 2090  2.0 327220 2333432 thunderbird
 1050  1.2 210988 737336 Xorg
22839  0.8 140308 3041640 chromium-browse
22992  0.7 125892 1731736 chromium-browse
 1885  0.5 92588 1365096 gnome-software
 1889  0.5 86460 998980 nautilus
 2117  0.5 83552 732476 gnome-system-mo
22908  0.4 79640 1083928 chromium-browse
23171  0.3 51144 1682216 chromium-browse
 2112  0.3 50252 1591588 pidgin
 2141  0.2 46620 686224 gnome-terminal-
 1831  0.2 45660 864244 evolution-calen
```

---

### Post by Doug S on 2017-12-06
> **mirzman said:**
> It's already use swap! But in the same time buff/cache=9321624
That is fairly normal, and just means that swap was used sometime since boot, but doesn't necessarily mean it is currently still needed.
Example:
```

root@DOUG-64:/home/doug# uptime
 07:39:43 up 14 days, 18:47,  6 users,  load average: 0.00, 0.00, 0.00

root@DOUG-64:/home/doug# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:        3070448      304048       82344       44400     2684056     2512732
Swap:       3133436        2364     3131072
              total        used        free      shared  buff/cache   available
Mem:        3070448      304192     2644680       44400      121576     2595160
Swap:       3133436        2364     3131072

root@DOUG-64:/home/doug# swapoff -a && swapon -a

root@DOUG-64:/home/doug# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:        3070448      306020     2630992       44408      133436     2587472
Swap:       3133436           0     3133436
              total        used        free      shared  buff/cache   available
Mem:        3070448      305804     2643156       44408      121488     2593640
Swap:       3133436           0     3133436

```

---

### Post by mirzman on 2017-12-06
> **Doug S said:**
> That is fairly normal, and just means that swap was used sometime since boot, but doesn't necessarily mean it is currently still needed.
But it's 9G of cache. It's no need to use swap.
It looks like Ubuntu tries to allocate disk cache in swap.

---

### Post by mirzman on 2017-12-06
A day and a half ago:
```
# uptime
 14:08:45 up 5 days,  2:40,  1 user,  load average: 0,64, 0,62, 0,60

root@mirzman-workstation:~# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:       16294632     4205164     2426264      755812     9663204     3893072
Swap:      16636924           0    16636924
              total        used        free      shared  buff/cache   available
Mem:       16294632     4201380     3759604      744948     8333648     3971136
Swap:      16636924           0    16636924
```
It's no swap

now:
```
root@mirzman-workstation:~# uptime
 19:14:32 up 6 days,  7:46,  1 user,  load average: 3,07, 2,61, 2,21

root@mirzman-workstation:~# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:       16294632     5811744      421048      704752    10061840      711260
Swap:      16636924      329724    16307200
              total        used        free      shared  buff/cache   available
Mem:       16294632     5824444      736364      710020     9733824      699140


```
Swap is increasing... Several days later system will go down.

---

### Post by Impavidus on 2017-12-06
I'm no specialist in memory management, but this seems a little odd to me. With 3.9GB available and 2.4GB free, it means that only 1.5GB of 9.6GB in buffers/cache can be reclaimed, which is a remarkably low fraction. Still, depending on what you're doing on that machine, there may be a sensible reason for that.

Maybe you can get some more detailed information from /proc/meminfo.```
cat /proc/meminfo
```

---

### Post by mirzman on 2017-12-07
It's already works veeeeery slow... I'll try to kill/restart some processes to stay system alive several days more.
```
root@mirzman-workstation:~# uptime
 11:21:30 up 6 days, 23:53,  1 user,  load average: 0,83, 0,80, 0,71
root@mirzman-workstation:~# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:       16294632     5418960      394748      418184    10480924      439672
Swap:      16636924     1225152    15411772
              total        used        free      shared  buff/cache   available
Mem:       16294632     5418420      554772      423144    10321440      478000
Swap:      16636924     1225152    15411772

```

> **Impavidus said:**
> Still, depending on what you're doing on  that machine, there may be a sensible reason for that.
I use browser (with a lot of open tabs), email client,  messaging services, terminal. It's all :(
It was top of processes by memory usage several messages ago.

> **Impavidus said:**
> Maybe you can get some more detailed information from /proc/meminfo.```
cat /proc/meminfo
```
```
root@mirzman-workstation:~# cat /proc/meminfo
MemTotal:       16294632 kB
MemFree:          468696 kB
MemAvailable:     460304 kB
Buffers:           12256 kB
Cached:           734940 kB
SwapCached:       101216 kB
Active:          4750596 kB
Inactive:        1173976 kB
Active(anon):    4622648 kB
Inactive(anon):  1074176 kB
Active(file):     127948 kB
Inactive(file):    99800 kB
Unevictable:          48 kB
Mlocked:              48 kB
SwapTotal:      16636924 kB
SwapFree:       15507864 kB
Dirty:               616 kB
Writeback:             0 kB
AnonPages:       5081936 kB
Mapped:           416636 kB
Shmem:            519460 kB
Slab:            9753604 kB
SReclaimable:      37532 kB
SUnreclaim:      9716072 kB
KernelStack:       13072 kB
PageTables:        59104 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    24784240 kB
Committed_AS:   13140304 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:   1284096 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      358212 kB
DirectMap2M:    16281600 kB
DirectMap1G:     1048576 kB
```

---

### Post by Impavidus on 2017-12-07
It seems your unreclaimable slab is excessively large. For comparison on my computer:```
$ cat /proc/meminfo
MemTotal:        8105308 kB
MemFree:         3333608 kB
MemAvailable:    4583560 kB
Buffers:          166308 kB
Cached:          1767816 kB
(...)
Slab:             147812 kB
SReclaimable:     108240 kB
SUnreclaim:        39572 kB
(...)

```Slab is for in-kernel data structures. As I said, I don't know the details of memory management. Do you, by any chance, use a non-standard kernel? Although you quoted 4.4.0-101-generic, which seems to be the standard on 16.04 and 14.04 with HWE. I imagine there might be a small memory leak in the kernel (but that should have been discovered) or some driver, but I don't feel capable providing more help with that.

And any particular reason to keep your computer running very slowly for a couple of days more instead of a simple reboot?

---

### Post by photonxp on 2017-12-08
> **mirzman said:**
> 

```

root@mirzman-workstation:~# ps --sort -rss -eo pid,pmem,rss,vsz,comm | head -20
  PID %MEM   RSS    VSZ COMMAND
 7392  5.7 939048 2968784 Web Content
 7164  4.4 720768 3052668 Web Content
 7121  4.3 713492 2926076 Web Content
... ...

```

What is "Web Content" here? Do you use it a lot or just occasionally? What is it running for? 
You can try killing "Web Content" and then run again the command:
```
free && sync && sudo sh -c "echo 3 > /proc/sys/vm/drop_caches" && free
```
You can run this command as non-root user then enter the password for root when it's required.

---

### Post by vasa1 on 2017-12-08
> **photonxp said:**
> What is "Web Content" here? ...
It originates from Firefox.

---

### Post by mirzman on 2017-12-08
It died :(
I tried echo 10000000 >/proc/sys/vm/min_free_kbytes
The result will be several days later

---

### Post by mirzman on 2017-12-08
> **Impavidus said:**
> Do you, by any chance, use a non-standard kernel? Although you quoted 4.4.0-101-generic, which seems to be the standard on 16.04 and 14.04 with HWE. I imagine there might be a small memory leak in the kernel (but that should have been discovered) or some driver, but I don't feel capable providing more help with that.

And any particular reason to keep your computer running very slowly for a couple of days more instead of a simple reboot?
Yes, I use standard software.
It's no reason, but my uptimes used to be 60 days several months ago, and restarting system every 3 days is something terrible for me now...

---

### Post by mirzman on 2017-12-08
> **photonxp said:**
> What is "Web Content" here? Do you use it a lot or just occasionally? What is it running for? 
You can try killing "Web Content" and then run again the command:
```
free && sync && sudo sh -c "echo 3 > /proc/sys/vm/drop_caches" && free
```
You can run this command as non-root user then enter the password for root when it's required.
It's firefox. I'll try this several days later when enough amount of memory will leak.

---

### Post by mirzman on 2017-12-08
> **mirzman said:**
> It died :(
I tried echo 10000000 >/proc/sys/vm/min_free_kbytes
The result will be several days later
System went to swap immediately... This don't work.
```
root@mirzman-workstation:~# uptime
 14:04:08 up 56 min,  1 user,  load average: 2,39, 1,60, 1,19
root@mirzman-workstation:~# cat /proc/sys/vm/min_free_kbytes
10000000
root@mirzman-workstation:~# free && sync && echo 3 > /proc/sys/vm/drop_caches && free
              total        used        free      shared  buff/cache   available
Mem:       16294664     1281416    14197052      429076      816196     1846350
Swap:      16636924     1257740    15379184
              total        used        free      shared  buff/cache   available
Mem:       16294664     1281576    14205440      428680      807648     1850532
Swap:      16636924     1257612    15379312
```

---

### Post by mirzman on 2017-12-15
> **photonxp said:**
> You can try killing "Web Content" and then run again the command:
```
free && sync && sudo sh -c "echo 3 > /proc/sys/vm/drop_caches" && free
```
You can run this command as non-root user then enter the password for root when it's required.

It don't help...

```
root@mirzman-workstation:~# free && sync && sudo sh -c "echo 3 > /proc/sys/vm/drop_caches" && free
              total        used        free      shared  buff/cache   available
Mem:       16294664     4663356      432936      597716    11198372     1134764
Swap:      16636924      576192    16060732
              total        used        free      shared  buff/cache   available
Mem:       16294664     4664364     1172776      578144    10457524     1206540
Swap:      16636924      576192    16060732

root@mirzman-workstation:~# killall -9 firefox

root@mirzman-workstation:~# ps --sort -rss -eo pid,pmem,rss,vsz,comm | awk '{sum+=$3}END{print sum}'
2886740

root@mirzman-workstation:~# ps --sort -rss -eo pid,pmem,rss,vsz,comm | head -20
  PID %MEM   RSS    VSZ COMMAND
 2092  1.9 321712 3001048 Telegram
22052  1.8 302164 2490956 chromium-browse
19246  1.7 285720 2376336 thunderbird
21898  1.3 225412 3171484 chromium-browse
 1037  0.8 134940 626540 Xorg
 2235  0.6 109484 1249884 compiz
 2113  0.5 87680 767204 gnome-system-mo
22034  0.5 85752 1118964 chromium-browse
 8157  0.5 83064 1714332 chromium-browse
 1892  0.4 66880 1305000 nautilus
 1888  0.3 64620 1367316 gnome-software
 2130  0.3 53492 724940 gnome-terminal-
23510  0.3 53184 1723176 chromium-browse
23980  0.2 46448 1699960 chromium-browse
22249  0.2 37656 2191820 chromium-browse
 1726  0.2 35264 736964 hud-service
10018  0.2 32860 1143852 gedit
 4645  0.1 31044 1650392 chromium-browse
22243  0.1 30928 2104872 chromium-browse

root@mirzman-workstation:~# free && sync && sudo sh -c "echo 3 > /proc/sys/vm/drop_caches" && free
              total        used        free      shared  buff/cache   available
Mem:       16294664     1958312     3720052      571324    10616300     3918284
Swap:      16636924      535036    16101888
              total        used        free      shared  buff/cache   available
Mem:       16294664     1954044     3958448      571028    10382172     3923780
Swap:      16636924      535032    16101892

```

---

