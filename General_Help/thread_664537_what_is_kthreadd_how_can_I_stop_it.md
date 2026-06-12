---
title: "what is kthreadd how can I stop it?"
date: 2008-01-11
forum: General Help
---

### Post by raevsky.andrei on 2008-01-11
Hi,

I am using a fully updated Ubuntu 7.10 Gutsy on x86 (kernel  2.6.22-14-rt).  I recently installed a number of audio and video editing applications.  I then noticed that when I did 'top' a number of new things (here in blue) showed up which I previously did not have:

```
 4773 root      20   0  167m  17m 7344 S  2.0  3.4   0:06.80 Xorg               
 6035 andrei    20   0 66252  16m  10m S  1.7  3.3   0:02.11 gnome-terminal     
 6076 andrei    20   0  2360 1168  876 R  0.7  0.2   0:02.02 top                
[COLOR="Blue"]   39 root     -51  -5     0    0    0 S  0.3  0.0   0:01.38 IRQ-9              
 3602 root     -51  -5     0    0    0 S  0.3  0.0   0:00.54 IRQ-11 [/COLOR]            
 5932 andrei    20   0 87540  17m  13m S  0.3  3.5   0:01.64 nautilus           
 5946 andrei    20   0 16464 2672 1760 S  0.3  0.5   0:00.14 gnome-screensav    
    1 root      20   0  2948 1852  532 S  0.0  0.4   0:01.93 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 posix_cpu_timer    
[COLOR="Blue"]    5 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-high/0     
    6 root     -51  -5     0    0    0 S  0.0  0.0   0:00.62 softirq-timer/0    
    7 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-net-tx/    
    8 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-net-rx/    
    9 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-block/0 [/COLOR]   
   10 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 softirq-tasklet
```

I had never seen this IRQ stuff before.  Turns out that all these are spawned by kthreadd.  I assume that this is some kind of kernel thing since the 'k' in it is unlikely to come from KDE as I use GNOME (with some KDE apps thrown in from time to time).

The system works fine, but this stuff clutters my top and that bothers me.  Since I had no idea what softirq was,  I looked it up and found [this]("http://lists.pdxlinux.org/pipermail/plug/2005-September/042934.html"):

> softirqs are software interrupts, used often by device drivers to do
further processing of something outside of the hardware interrupt
handler, which needs to run as fast as possible so interrupts can be
re-enabled.  Perhaps you have some rogue hardware?  Does
/proc/interrupts show something going crazy?  Is the box receiving a
lot of network traffic?  Anything in your logs?

My /proc/interrupts is empty, I get no special traffic, my logs are normal, and I did not add any weird or exotic hardware.

I tried shooting kthreadd (using killall), but is stays and continues running.

I then uninstalled all the video and audio stuff I had played with, but that changed nothing.  All the new stuff still cluttters my top and that bothers me as I always have top running in a terminal to see how my system behaves.

Anyway, could anyone please tell me what these processes are, what the kthreadd daemon does for a living, if/how I can get rid of it?

Many thanks,

Andrei

---

### Post by metator on 2008-01-24
kthreadd - kernel thread daemon, the parent of all kernel threads. I believe it is not possible to kill this daemon. kthreadd assumes PID #2 and is created by the init process. 
I would also like to know more about it, but that's the only info i was able to gather.

---

### Post by metator on 2008-01-28
More info at: 
[ kthread: run kthreadd with max priority SCHED_FIFO]("http://groups.google.com.br/group/linux.kernel/browse_thread/thread/c1ccebfaa7ad24d3/f6c0241d542fd9cc?lnk=gst&q=kthreadd#f6c0241d542fd9cc")

---

