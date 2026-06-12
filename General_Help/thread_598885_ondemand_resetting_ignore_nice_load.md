---
title: "ondemand resetting ignore_nice_load"
date: 2007-10-31
forum: General Help
---

### Post by notfred on 2007-10-31
I'm using 7.10 x86_64 on a Q6600. My problem is that I want the processor to run at full speed when niced processes are running. I checked and my CPU is speedstep'd down:
```
nreilly@nick:~$ grep Hz /proc/cpuinfo 
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
cpu MHz         : 1596.000
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
cpu MHz         : 1596.000
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
cpu MHz         : 1596.000
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
cpu MHz         : 1596.000
nreilly@nick:~$
```

I have nice'd processes running:
```
nreilly@nick:~$ top

top - 19:13:26 up 3 days, 20:01,  2 users,  load average: 2.51, 2.58, 2.65
Tasks: 154 total,   1 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.1%us,  5.3%sy, 60.4%ni, 32.4%id,  0.0%wa,  0.0%hi,  1.6%si,  0.0%st
Mem:   2054020k total,  1986964k used,    67056k free,    90676k buffers
Swap:  1951888k total,    38352k used,  1913536k free,  1381240k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
26099 nreilly   34  19 38720 9856 1996 S   96  0.5 770:48.98 FahCore_a1.exe     
26100 nreilly   34  19 37520 8612 1900 S   59  0.4 465:45.59 FahCore_a1.exe     
26101 nreilly   34  19 37460 8528 1840 S   53  0.4 437:32.68 FahCore_a1.exe     
26102 nreilly   34  19 37460 8520 1840 S   53  0.4 432:58.62 FahCore_a1.exe    
```

So I become root and then set ignore_nice_load to off in the ondemand governor:
```
  echo 0 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
  echo 0 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/ignore_nice_load
  echo 0 > /sys/devices/system/cpu/cpu2/cpufreq/ondemand/ignore_nice_load
  echo 0 > /sys/devices/system/cpu/cpu3/cpufreq/ondemand/ignore_nice_load

```

This works for a while, if I read back ignore_nice_load it is indeed set to 0 and my cores step up to the full 2.4GHz. After a few hours though, I notice my processors are back down at 1.6GHz and ignore_nice_load has gone back to 1 on all the processors.

I don't have cpufreqd or powernowd running:
```
nreilly@nick:~$ ps -elf | grep powernowd
0 S nreilly  28575 28355  0  78   0 -  1280 pipe_w 19:17 pts/0    00:00:00 grep powernowd
nreilly@nick:~$ ps -elf | grep cpufreqd
0 S nreilly  28577 28355  0  78   0 -  1279 pipe_w 19:17 pts/0    00:00:00 grep cpufreqd

```

But I do seem to have some hal thing related to cpufreq running:
```
nreilly@nick:~$ ps -elf | grep cpufreq
0 S root      7260  7203  0  75   0 -  4433 834463 Oct27 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
0 S nreilly  28570 28355  0  78   0 -  1280 pipe_w 19:16 pts/0    00:00:00 grep cpufreq
nreilly@nick:~$
```

Any idea on how to get the ignore_nice_load to stick? Or at least what might be resetting it? I don't see any cron jobs that may reset it either.

---

### Post by jdi on 2007-11-24
Answer is a gconf setting in gnome-power-manager.  Check:
    [http://ubuntuforums.org/archive/index.php/t-505325.html](http://ubuntuforums.org/archive/index.php/t-505325.html)

---

