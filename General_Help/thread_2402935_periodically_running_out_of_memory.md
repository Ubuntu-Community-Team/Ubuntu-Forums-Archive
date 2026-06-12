---
title: "periodically running out of memory"
date: 2018-10-05
forum: General Help
---

### Post by mattdawolf on 2018-10-05
Not sure why xenial is running out of memory with 32 gigs of RAM. Can anyone find the root cause in this dmesg?

[https://paste.ubuntu.com/p/7cP5Mfz5VH/](https://paste.ubuntu.com/p/7cP5Mfz5VH/)

---

### Post by Autodave on 2018-10-05
I have very little idea what any of that means. Sorry.  But let's maybe get some info for the next person that responds......

Is this a dual boot or single boot?  Are you running this as a virtual machine?  What programs are you running?

I only have 8 gig in this machine and I have tried to max it out and have not even come close.

---

### Post by #&amp;thj^% on 2018-10-05
> **Autodave said:**
> 
I only have 8 gig in this machine and I have tried to max it out and have not even come close.
+1 Here also.
I wish i had a definitive answer for you but. 
By default, Linux kernels allow processes to request more memory than currently available in the system. This makes all the sense in the world, considering that most of the processes never actually use all of the memory they allocate.

FTR: I rarely run swap even on this smaller machine I'm running today, **and I notice that you are using a "zswap"**:
```
free -m
              total        used        free      shared  buff/cache   available
Mem:           7655        1144        5437         173        1073        6100
Swap:             0           0           0

```
I now have 10 tabs open in firefox streaming a news chanel with:
```
 cat /proc/meminfo | grep MemAvailable
MemAvailable:    6213924 kB

```

A little more to see:
```
vmstat -s
      7839488 K total memory
      1188236 K used memory
      1421756 K active memory
       614540 K inactive memory
      5539124 K free memory
        44076 K buffer memory
      1068052 K swap cache
            0 K total swap
            0 K used swap
            0 K free swap
        49696 non-nice user cpu ticks
          461 nice user cpu ticks
        24822 system cpu ticks
      1976968 idle cpu ticks
        50555 IO-wait cpu ticks
            0 IRQ cpu ticks
         2115 softirq cpu ticks
            0 stolen cpu ticks
      1272005 pages paged in
       380457 pages paged out
            0 pages swapped in
            0 pages swapped out
      6094599 interrupts
     13168310 CPU context switches
   1538766346 boot time
        79142 forks

```
Maybe have a look here but make sure you have a good understanding of what is said: [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/performance_tuning_guide/s-memory-captun](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/performance_tuning_guide/s-memory-captun)

just my 2 cents worth

---

### Post by oldrocker99 on 2018-10-05
Certain programs take up as much memory as you have. If it's not a necessary program, for example if you have a download manager which is taking all of your RAM, you can kill the browser, which isn't needed for the manager. That will free up some RAM. This was happening to me, and I just got 16GB for my laptop. So far so good,

I **highly** recommend htop, which makes killing a process easy, with F3 for search, and F9 to kill. It's like top on steroids.

---

