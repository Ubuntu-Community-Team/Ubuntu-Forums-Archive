---
title: "Speeding up or slowing down a cpu and memory?"
date: 2023-07-06
forum: General Help
---

### Post by josephchrzempiec on 2023-07-06
Hello, I'm going to be soon building a new server. A used server but new to me. I was curious about something. The cpu I have takes a lot of power and most of the time it will just sit there idling. I was wondering If it is possible to save a little power. I have researching online a few things that came up was to slow down a CPU speed as well as memory. That I'm curious about that and wondering if it the best way to go how would I do that. I'm asking the community if that is the best way to go to save a little power without having to shutoff cores and take out some memory?

I have in the past figure out how to shut off cores. Figured out that wasn't the best way to go and needed them cores and memory. I'm trying to get the community advice on what would be a better way.

Josrph

---

### Post by MAFoElffen on 2023-07-06
The Linux Kernel has it's own way of handling CPU Core power states... and idle conditions. For server I limit the cstates that the CPU can go down to... Reason being is that I don't want the CPU to power down into a sleep state...

The name of the game in Server is availability and latent response. Not in power savings, sleep and hibernation states.

(Bad) Experience showed me that when the CPU of my server powered down, that my ZFS vdevs dropped out one by one and became unavailable, and then degraded the pools. Which was bad juju. I since then keep my powerstates above a certain level to prevent that. Other may have a different experience and views on that, but for me, I found that to be a very bad experience to be trying to save a limited amount of money.

Spun disks of yester-year generated a lot of heat and used more power than silicon storage is now. I don't use much power in comparison using SSD and NVMe storage pools.

---

### Post by Doug S on 2023-07-06
There is an entire kernel sub-group, linux power managment, dedicated to saving energy while at the same time ensuring fast system response to power hungry tasks. You shouldn't have to do anything at all to ensure low power consumption during idle times.

Example for my Ubuntu test server, 20.04.6: Step function load from idle. Mains power when idle was 40.0 watts, and during high load 179.5 watts. Processor package power went from ~1.85 watts to a throttled limited ~125 watts. intel_pstate CPU frequency scaling driver and powersave governor (the default). Processor: Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz

```
doug@s19:~$ sudo /home/doug/kernel/linux/tools/power/x86/turbostat/turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgWatt,PkgTmp --interval 15
Busy%   Bzy_MHz PkgTmp  PkgWatt
0.02    1277    36      1.92
0.01    800     36      1.88
0.01    800     37      1.80
0.02    800     37      1.88
0.01    800     37      1.77
67.60   4479    68      88.57
98.70   4475    70      129.24
99.44   4465    71      125.46
99.57   4466    72      124.91
```

---

### Post by josephchrzempiec on 2023-07-06
> **MAFoElffen said:**
> The Linux Kernel has it's own way of handling CPU Core power states... and idle conditions. For server I limit the cstates that the CPU can go down to... Reason being is that I don't want the CPU to power down into a sleep state...

The name of the game in Server is availability and latent response. Not in power savings, sleep and hibernation states.

(Bad) Experience showed me that when the CPU of my server powered down, that my ZFS vdevs dropped out one by one and became unavailable, and then degraded the pools. Which was bad juju. I since then keep my powerstates above a certain level to prevent that. Other may have a different experience and views on that, but for me, I found that to be a very bad experience to be trying to save a limited amount of money.

Spun disks of yester-year generated a lot of heat and used more power than silicon storage is now. I don't use much power in comparison using SSD and NVMe storage pools.


Thank you very much for helping me to understand. Yes I also have old drives. I'm thinking of changing them out to SSD. But the problem is cost. I know SSD and NVME drives has come down a lot. But still a hafty cost right now for me. Still looking into other things as well. I'm also looking maybe changing out CPU to a newer one which is cheap because its a older design of Xeon.  but my CPU is 185watts. The next one is about 95 to 90 watts. Again cost me my problem not having enough money for things being that how things are still where I'm at and work is hard to find. 

Meanwhile I'm looking at software side of things to see if there is something I can save in power.

---

### Post by josephchrzempiec on 2023-07-06
> **Doug S said:**
> There is an entire kernel sub-group, linux power managment, dedicated to saving energy while at the same time ensuring fast system response to power hungry tasks. You shouldn't have to do anything at all to ensure low power consumption during idle times.

Example for my Ubuntu test server, 20.04.6: Step function load from idle. Mains power when idle was 40.0 watts, and during high load 179.5 watts. Processor package power went from ~1.85 watts to a throttled limited ~125 watts. intel_pstate CPU frequency scaling driver and powersave governor (the default). Processor: Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz

```
doug@s19:~$ sudo /home/doug/kernel/linux/tools/power/x86/turbostat/turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgWatt,PkgTmp --interval 15
Busy%   Bzy_MHz PkgTmp  PkgWatt
0.02    1277    36      1.92
0.01    800     36      1.88
0.01    800     37      1.80
0.02    800     37      1.88
0.01    800     37      1.77
67.60   4479    68      88.57
98.70   4475    70      129.24
99.44   4465    71      125.46
99.57   4466    72      124.91
```


The problem I have is that I have a 8 core 16 thread processor. At least any given time 8 maybe 10 of the threads are being used. The other cores are not doing anything at all. And yet the CPU  speed is at full max 3.4GHz. Now I'm not sure if that is the same for the cores and threads that is doing anything or not.

---

### Post by Doug S on 2023-07-06
> **josephchrzempiec said:**
> The problem I have is that I have a 8 core 16 thread processor. At least any given time 8 maybe 10 of the threads are being used. The other cores are not doing anything at all. And yet the CPU  speed is at full max 3.4GHz. Now I'm not sure if that is the same for the cores and threads that is doing anything or not.Shouldn't be a problem. My original example was a very simple one, adding 12 threads to my 6 core 12 CPU processor all at once. Here is another example adding one 100% load single thread every 60 seconds:

```
doug@s19:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgWatt,PkgTmp --interval 15
Busy%   Bzy_MHz PkgTmp  PkgWatt
0.04    800     37      1.99
0.02    800     37      2.00
0.05    1831    37      2.09
0.01    800     37      2.06
7.26    4795    53      24.84
8.35    4800    53      28.25
8.35    4800    55      28.21
8.35    4800    55      28.11
15.61   4800    56      38.95
16.70   4800    56      40.70
16.66   4800    57      40.67
16.66   4800    58      40.82
23.95   4800    61      51.09
24.97   4800    62      52.44
24.98   4800    61      52.51
24.97   4800    61      52.74
32.30   4800    63      62.30
33.29   4800    65      63.50
33.28   4800    65      63.67
33.29   4800    66      64.02
40.63   4737    66      68.60
41.56   4703    65      67.74
41.59   4701    66      68.30
41.60   4700    67      68.49
48.99   4700    66      72.98
49.91   4700    67      73.57
49.91   4700    68      73.68
49.91   4700    68      73.87
57.33   4700    71      73.69
58.22   4700    72      73.88
58.22   4700    72      73.76
58.22   4700    72      73.91
65.68   4700    72      74.10
66.53   4700    72      73.91
66.53   4700    73      73.96
66.53   4700    72      73.99
74.03   4700    72      74.23
74.85   4700    73      74.25
74.85   4700    72      74.29
74.85   4700    72      74.17
82.37   4700    72      74.41
83.16   4700    73      74.23
83.16   4700    72      74.46
83.16   4700    72      74.60
90.72   4700    72      74.35
91.47   4700    72      74.05
91.47   4700    72      74.59
91.47   4700    72      74.47
99.04   4700    72      74.37
99.76   4700    72      74.28
99.76   4700    72      74.29
99.76   4700    72      74.45
99.76   4700    71      74.33
```The CPU frequency drop to 4.7 GHz was due to this (from turbostat without the --quiet option):
```
cpu10: MSR_TURBO_RATIO_LIMIT: 0x2f3030303030
[COLOR="#FF0000"]47 * 100.0 = 4700.0 MHz max turbo 6 active cores[/COLOR]
48 * 100.0 = 4800.0 MHz max turbo 5 active cores
48 * 100.0 = 4800.0 MHz max turbo 4 active cores
48 * 100.0 = 4800.0 MHz max turbo 3 active cores
48 * 100.0 = 4800.0 MHz max turbo 2 active cores
48 * 100.0 = 4800.0 MHz max turbo 1 active cores
``` I never hit power or thermal limit throttling.

EDIT: Another example: adding a thread with very low load at 73 Hertz work/sleep frequency once every 0.25 seconds:

```
$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgWatt,PkgTmp --interval 15
Busy%   Bzy_MHz PkgTmp  PkgWatt
0.02    1213    41      2.03
0.01    800     40      2.04
0.01    800     40      2.04
4.13    800     40      2.47
12.10   800     40      2.91
3.74    4079    44      21.90
4.58    4700    45      24.74
5.91    4700    44      26.73
7.16    4700    46      28.26
8.47    4700    47      30.10
9.83    4700    47      31.79
11.33   4700    48      33.29
12.87   4700    50      34.95
14.25   4700    51      36.52
15.82   4700    52      37.93
17.36   4700    53      39.53
19.03   4700    53      41.24
20.52   4700    54      42.72
22.17   4700    55      44.19
23.73   4700    55      45.70
25.43   4700    57      47.39
27.02   4700    59      49.21
28.73   4700    60      51.04
30.51   4700    59      52.48
32.52   4700    60      54.40
34.25   4700    61      55.97
36.03   4700    63      57.61
37.83   4700    64      59.11
39.61   4700    65      60.80
41.58   4700    66      62.70
43.45   4700    68      64.24
45.38   4700    68      65.72
47.46   4700    69      67.56
49.63   4700    70      69.33
51.74   4700    71      71.26
53.97   4700    72      72.83
56.18   4700    72      74.49
58.49   4700    73      75.93
60.87   4700    73      77.29
63.26   4700    73      78.94
65.68   4700    73      80.16
68.07   4700    74      81.66
70.43   4700    72      83.11
72.88   4700    73      84.59
75.36   4700    73      86.05
77.94   4700    73      87.45
80.54   4700    74      88.78
83.08   4700    74      89.98
85.63   4700    73      90.98
88.15   4700    73      92.14
90.57   4700    74      93.33
92.93   4700    74      94.28
95.10   4700    74      95.38
96.88   4700    74      95.83
98.71   4700    74      96.27
99.71   4700    74      96.36
99.76   4700    74      96.66
99.76   4700    74      96.90
```
Changing to the intel_cpufreq (intel_pstate in passive mode) CPU frequency scaling driver and the schedutil governor seems to help with the lower end for the above example:

```
$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgWatt,PkgTmp --interval 15
Busy%   Bzy_MHz PkgTmp  PkgWatt
0.00    3931    42      2.33
1.91    1144    42      3.29
8.29    1001    42      3.49
15.04   967     42      3.95
22.36   966     42      4.38
29.34   995     43      4.96
34.62   1070    44      5.75
20.41   2020    43      9.69
14.12   3307    44      13.80
15.51   3431    45      14.85
15.78   3796    45      20.94
16.95   3982    49      25.13
15.68   4700    51      37.56
17.07   4700    51      39.33
18.58   4700    53      40.86
20.20   4700    53      42.59
21.83   4700    54      44.26
23.29   4700    55      45.97
```

---

### Post by metallinux on 2023-07-07
[COLOR=#C8C3BC][FONT=&amp]Hi Joseph,
[/FONT][/COLOR]
[COLOR=#C8C3BC][FONT=&amp]I hope you're doing well and I had a follow up question please. What everyone has provided her in regards to CPU Core Power States is excellent and has given me a lot of information myself.
[/FONT][/COLOR]
[COLOR=#C8C3BC][FONT=&amp]Regarding your used server that you are going to build:
[/FONT][/COLOR]
[COLOR=#C8C3BC][FONT=&amp]What were you planning on buying please? Was it an old Supermicro, Dell, HP etc server or just off-the-shelf consumer parts and placing those into a desktop/server case?
[/FONT][/COLOR]
[COLOR=#C8C3BC][FONT=&amp]Many thanks and I look forward to hearing from you and helping further.
[/FONT][/COLOR]
[COLOR=#C8C3BC][FONT=&amp]Metallinux[/FONT][/COLOR]

---

### Post by josephchrzempiec on 2023-07-16
Hello all, Sorry I was in the Hosptial for some time. My health is not so good at this moment. I'm learning all I can for this idea I have on the CPU and memory speeding up and slowing down. In the next few days I will have osme follow up questions. Thank you for the help.

---

