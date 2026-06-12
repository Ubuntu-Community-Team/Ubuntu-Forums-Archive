---
title: "How to enable second core in Hardy 64bit?"
date: 2008-05-22
forum: General Help
---

### Post by Suky on 2008-05-22
Hi,

I have run mpstat and return the result as

```
mpstat -P ALL 5
Linux 2.6.24-16-generic (subuntu) 	05/22/2008

01:54:48 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:54:53 PM  all   33.53    0.00    6.83    0.40    0.00    0.00    0.00   59.24    307.20
01:54:53 PM    0   33.53    0.00    6.83    0.40    0.00    0.00    0.00   59.24    307.20
01:54:53 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:54:53 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:54:58 PM  all   25.85    0.00    8.22    0.80    0.00    0.00    0.00   65.13    212.40
01:54:58 PM    0   25.85    0.00    8.22    0.80    0.00    0.00    0.00   65.13    212.40
01:54:58 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:54:58 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:03 PM  all   36.65    9.16    6.57    2.19    0.60    0.00    0.00   44.82    259.60
01:55:03 PM    0   36.65    9.16    6.57    2.19    0.60    0.00    0.00   44.82    259.60
01:55:03 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:03 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:08 PM  all   41.20   15.00    9.20    5.60    0.20    0.00    0.00   28.80    287.60
01:55:08 PM    0   41.20   15.00    9.20    5.60    0.20    0.00    0.00   28.80    287.60
01:55:08 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:08 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:13 PM  all   49.50    0.80   14.57   18.56    0.80    0.20    0.00   15.57    323.20
01:55:13 PM    0   49.50    0.80   14.57   18.56    0.80    0.20    0.00   15.57    323.40
01:55:13 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:13 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:18 PM  all   21.80    0.00    4.20    4.80    0.00    0.00    0.00   69.20    217.40
01:55:18 PM    0   21.80    0.00    4.20    4.80    0.00    0.00    0.00   69.20    217.20
01:55:18 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:18 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:23 PM  all   17.76    0.00    3.39    0.80    0.00    0.00    0.00   78.04    151.90
01:55:23 PM    0   17.76    0.00    3.39    0.80    0.00    0.00    0.00   78.04    151.90
01:55:23 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:23 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:28 PM  all    8.00    0.00    2.60    0.00    0.00    0.00    0.00   89.40    115.60
01:55:28 PM    0    8.00    0.00    2.60    0.00    0.00    0.00    0.00   89.40    115.60
01:55:28 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:28 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:33 PM  all   12.22    0.00    5.41    2.00    0.00    0.00    0.00   80.36    148.00
01:55:33 PM    0   12.22    0.00    5.41    2.00    0.00    0.00    0.00   80.36    148.00
01:55:33 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:33 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:38 PM  all   14.80    0.20    7.40    8.20    0.40    0.00    0.00   69.00    168.00
01:55:38 PM    0   14.80    0.20    7.40    8.20    0.40    0.00    0.00   69.00    168.00
01:55:38 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:38 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:43 PM  all   25.85    0.00    5.01    0.80    0.00    0.00    0.00   68.34    213.80
01:55:43 PM    0   25.85    0.00    5.01    0.80    0.00    0.00    0.00   68.34    213.80
01:55:43 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:43 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:48 PM  all   19.12    0.00    4.18    1.39    0.20    0.00    0.00   75.10    175.40
01:55:48 PM    0   19.12    0.00    4.18    1.39    0.20    0.00    0.00   75.10    175.40
01:55:48 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:48 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:53 PM  all   18.44    0.00    2.81    2.00    0.00    0.00    0.00   76.75    221.60
01:55:53 PM    0   18.44    0.00    2.81    2.00    0.00    0.00    0.00   76.75    221.60
01:55:53 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:53 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:55:58 PM  all   20.80    0.00    3.60    1.60    0.00    0.00    0.00   74.00    205.00
01:55:58 PM    0   20.80    0.00    3.60    1.60    0.00    0.00    0.00   74.00    205.00
01:55:58 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:55:58 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:03 PM  all   11.60    0.00    5.20    0.00    0.00    0.00    0.00   83.20    172.40
01:56:03 PM    0   11.60    0.00    5.20    0.00    0.00    0.00    0.00   83.20    172.40
01:56:03 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:03 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:08 PM  all   19.64    0.00    5.61    0.00    1.40    0.00    0.00   73.35    178.80
01:56:08 PM    0   19.64    0.00    5.61    0.00    1.40    0.00    0.00   73.35    178.80
01:56:08 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:08 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:13 PM  all   22.55    0.00    3.79    4.39    0.20    0.00    0.00   69.06    203.80
01:56:13 PM    0   22.55    0.00    3.79    4.39    0.20    0.00    0.00   69.06    203.80
01:56:13 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:13 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:18 PM  all   16.23    0.20    4.21    1.00    0.00    0.00    0.00   78.36    146.80
01:56:18 PM    0   16.23    0.20    4.21    1.00    0.00    0.00    0.00   78.36    146.80
01:56:18 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:18 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:23 PM  all    3.21    0.00    2.61   69.54    0.00    0.00    0.00   24.65    183.80
01:56:23 PM    0    3.21    0.00    2.61   69.54    0.00    0.00    0.00   24.65    183.80
01:56:23 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:23 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:28 PM  all    6.39    0.00    2.20   83.83    0.00    0.00    0.00    7.58    205.80
01:56:28 PM    0    6.39    0.00    2.20   83.83    0.00    0.00    0.00    7.58    206.00
01:56:28 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:28 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:33 PM  all   27.80    0.00    4.80   66.80    0.40    0.20    0.00    0.00    328.20
01:56:33 PM    0   27.80    0.00    4.80   66.80    0.40    0.20    0.00    0.00    328.00
01:56:33 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:33 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:38 PM  all   18.60    0.20    6.80   67.20    0.20    0.20    0.00    6.80    446.60
01:56:38 PM    0   18.60    0.20    6.80   67.20    0.20    0.20    0.00    6.80    446.60
01:56:38 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:38 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:43 PM  all   16.97    0.00    5.79   77.05    0.00    0.20    0.00    0.00    339.20
01:56:43 PM    0   16.97    0.00    5.79   77.05    0.00    0.20    0.00    0.00    339.20
01:56:43 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:43 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:48 PM  all   11.20    0.00    2.40   86.20    0.00    0.20    0.00    0.00    309.20
01:56:48 PM    0   11.20    0.00    2.40   86.20    0.00    0.20    0.00    0.00    309.20
01:56:48 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:48 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:53 PM  all   14.94    0.00    2.59   75.30    0.00    0.00    0.00    7.17    276.60
01:56:53 PM    0   14.94    0.00    2.59   75.30    0.00    0.00    0.00    7.17    276.60
01:56:53 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:53 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:56:58 PM  all    9.64    0.00    3.01   87.35    0.00    0.00    0.00    0.00    277.60
01:56:58 PM    0    9.64    0.00    3.01   87.35    0.00    0.00    0.00    0.00    277.60
01:56:58 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:56:58 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:57:03 PM  all   23.00    0.00    8.80   67.60    0.40    0.20    0.00    0.00    308.20
01:57:03 PM    0   23.00    0.00    8.80   67.60    0.40    0.20    0.00    0.00    308.20
01:57:03 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:57:03 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:57:08 PM  all   12.42    0.00    7.62   68.54    0.00    0.00    0.00   11.42    218.60
01:57:08 PM    0   12.42    0.00    7.62   68.54    0.00    0.00    0.00   11.42    218.60
01:57:08 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:57:08 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:57:13 PM  all   45.31    0.00    9.78    0.60    0.20    0.00    0.00   44.11    244.20
01:57:13 PM    0   45.31    0.00    9.78    0.60    0.20    0.00    0.00   44.11    244.20
01:57:13 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:57:13 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:57:18 PM  all   44.29    0.20    6.01    0.20    0.00    0.00    0.00   49.30    202.60
01:57:18 PM    0   44.29    0.20    6.01    0.20    0.00    0.00    0.00   49.30    202.60
01:57:18 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:57:18 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:57:23 PM  all    7.39    0.00    2.00    0.00    0.00    0.00    0.00   90.62    115.20
01:57:23 PM    0    7.39    0.00    2.00    0.00    0.00    0.00    0.00   90.62    115.20
01:57:23 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00

01:57:23 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
01:57:28 PM  all    9.40    0.00    6.20    0.20    0.20    0.00    0.00   84.00    143.80
01:57:28 PM    0    9.40    0.00    6.20    0.20    0.20    0.00    0.00   84.00    143.80
01:57:28 PM    1    0.00    0.00    0.00    0.00    0.00    0.00    0.00    0.00      0.00


```

And output of dmesg was
```
 dmesg | grep SMP
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[   17.070312] SMP alternatives: switching to UP code
[   17.557689] SMP motherboard not detected.
[   17.557700] SMP disabled

```

Output of /proc/cpuinfo was
```
 cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 72
model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-52
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
bogomips	: 1597.38
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```

It's look like Hardy know my notebook is dualcore processor but can't enable.
Have anyone help to solve or explain if i misunderstand about AMD dualcore?

Thanks,

---

### Post by jespdj on 2008-05-22
Have a look at the BIOS settings of your computer. It's possible that there's a wrong setting there - you'll have to look around the settings to see if there's anything about enabling multiple cores etc.

---

### Post by Suky on 2008-05-22
I have look around in my BIOS setting page and no parameters in BIOS that related to.

---

### Post by Suky on 2008-05-27
Solved with take "noapic" off from boot option.

---

