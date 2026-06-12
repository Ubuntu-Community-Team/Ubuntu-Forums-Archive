---
title: "Ubuntu freeze when low memory"
date: 2018-03-20
forum: General Help
---

### Post by drolman on 2018-03-20
Hi. My ubuntu server worked for one month without any problem. But last week I had to start programs which need more ram. And when free memory is around 100MB, system completelly freeze. I cant type anything, move cursor, connect from putty.. simply nothing.. but strange is, that hard drive is still working(is blinking).. I can fully reproduce this problem and it accurs almost every time when free memory is around 100MB. But I have swap file, and in this swap file is enough free space.. Here is my memory status 1 second before it freezed.

```

Every 1.0s free -mh                                               Mon Mar 19 17:05:33 2018                                     

               total         used          free         shared      buff/cache     available
Mem:             11G         10G           115M          1.2G             1.5G         115M
Swap:           7.9G        2.4G           5.5G          

```

Here is my linux kernel
```

Linux xxx 4.15.1-041501-generic #201802031831 SMP Sat Feb 3 18:32:13 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

Here is my linux version
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 17.10
Release:        17.10
Codename:       artful

```

Here is my swappines, overcommit_memory and overcommit_ratio configuration

```

vm.swappiness = 60
vm.overcommit_memory = 0
vm.overcommit_ratio = 50



```

Here is my hardware configuration
```

Motherboard: PRIME B350-PLUS
CPU            : AMD Ryzen 7 1700 Eight-Core Processor
RAM           : 4GB + 8GB DDR4
Hard drive  : Samsung 960 evo 250GB

```

Of course, I can upgrade my memory to 16GB, but still i want to have my system stable. Does anyone have some idea what could be wrong?

---

### Post by kerry_s on 2018-03-20
my guess is its swapping, moving memory to disk to make room. thats why the hd would show activity

---

### Post by drolman on 2018-03-20
Yes, it is possible. But i have fast HD (potentially [COLOR=#333333][FONT=Arial]1800 MB/s) and [/FONT][/COLOR]the system freezes forever. And as you can see, in the swap are already some data, so swap should work.

---

### Post by kerry_s on 2018-03-20
how long does the freeze last?

---

### Post by drolman on 2018-03-20
It froze for half hour, then I restarted it.

---

### Post by kerry_s on 2018-03-20
i think your just maxing out your ram, like you said you require more ram for certain apps.
a: add more ram to keep up with what you want to run
or
b: run less apps

you have 11gb available to use & your using 10gb of it. you want at least 2gb free to keep the system going. 

i only get that kind of use running several vm's.

---

### Post by TheFu on 2018-03-21
The early Ryzon CPUs had issues on Linux when they got busy.  Do you have one of the newer CPUs which fixed that issue? [http://www.extremetech.com/computing/254750-amd-replaces-ryzen-cpus-users-affected-rare-linux-bug](http://www.extremetech.com/computing/254750-amd-replaces-ryzen-cpus-users-affected-rare-linux-bug)

There is a point where low amounts of REAL RAM are a limit.  100MB ain't much.  Seems that reducing the RAM used for buffering some should be possible. Have you tried that?

---

### Post by drolman on 2018-03-23
Unfortunatelly I don`t have any newer CPU now, so I can`t try it. But thanks for possible solution. If I buy a new processor I will write the results here.

---

### Post by TheFu on 2018-03-23
> **drolman said:**
> Unfortunatelly I don`t have any newer CPU now, so I can`t try it. But thanks for possible solution. If I buy a new processor I will write the results here.

AMD provided free replacements. It was a design/manufacturing defect.  There should be ways to determine which batch your CPU was from and if it is known to have the issue or not. lscpu or /proc/cpuinfo might have some way to tell.

For example, my Core i3 has this in cpuinfo:
```
bugs            : cpu_meltdown spectre_v1 spectre_v2

``` which means that the pushed patches haven't corrected the issue on this machine.  I have no idea if AMD CPUs would see similar reporting from the kernel.

I'm seeing similar across all my Intel systems.  I don't own any AMD ... only because DDR4 RAM is too expensive. I've wanted to build a new Ryzen box since July, but can't get the performance and RAM I want for the price I need. It isn't the CPU or motherboard costs - it is the RAM that is way, way, way too expensive.  Any AMD CPU purchased from a reputable store since September shouldn't have the issue.  Those would have been returned to AMD already.  The 2nd-hand market is different. Shouldn't be hard to check yourself.

But we don't know that your system has this issue. It is just a place to start looking and eliminate from consideration.

---

### Post by drolman on 2018-03-27
It seems, that this is not this type of bug :( . I bought ryzen from reputable store at the end of November .. 

> **TheFu said:**
> AMD provided free replacements. It was a design/manufacturing defect.  There should be ways to determine which batch your CPU was from and if it is known to have the issue or not. lscpu or /proc/cpuinfo might have some way to tell.

For example, my Core i3 has this in cpuinfo:
```
bugs            : cpu_meltdown spectre_v1 spectre_v2

``` which means that the pushed patches haven't corrected the issue on this machine.  I have no idea if AMD CPUs would see similar reporting from the kernel.

I'm seeing similar across all my Intel systems.  I don't own any AMD ... only because DDR4 RAM is too expensive. I've wanted to build a new Ryzen box since July, but can't get the performance and RAM I want for the price I need. It isn't the CPU or motherboard costs - it is the RAM that is way, way, way too expensive.  Any AMD CPU purchased from a reputable store since September shouldn't have the issue.  Those would have been returned to AMD already.  The 2nd-hand market is different. Shouldn't be hard to check yourself.

But we don't know that your system has this issue. It is just a place to start looking and eliminate from consideration.

---

### Post by TheFu on 2018-03-27
> **drolman said:**
> It seems, that this is not this type of bug :( . I bought ryzen from reputable store at the end of November ..

Trust, but verify.  I'd check it.

---

### Post by strixtux on 2018-03-28
If it helps: I used to have similar symptoms on my 64 bit machine, AMD CPU, 250 GB HDD, 2 GB RAM running Ubuntu Studio 17.10. Sometimes all I could see was the spinning wheel, everything frozen, HDD working on Warp 10. This gridlock could be broken but by forced restart. I would know when to expect freezing: at boot, the entire graphic display would be sluggish. Then a few minutes of doing more than breathe, it would freeze. After reboot it would sometimes work as if nothing had happened - unless I'd start the browser, then it would freeze again.
I blame it on the NVIDIA on board graphic.
Solution: install of 18.04 beta. Works like a charm ever since. Even goes internet.
Maybe an inspiration...

---

