---
title: "[SOLVED] 7.10 (Gutsy) Mouse Stuttering"
date: 2008-02-26
forum: General Help
---

### Post by hmGIR on 2008-02-26
I'm fairly new to Linux, but not so new as that I don't know anything *at all*. But I digress: I installed Gutsy on my home Desktop after having used in an A+ Certification course at my school (I'd used other distros of Linux and Ubuntu before, but I'd never installed it on my home Desktop). Everything worked at fine (I was a little OCD about formatting and somehow killed my 80GB Primary drive, but that really doesn't seem to be part of the problem); in fact, everything STILL works fine, except for all of a sudden my mouse (USB) stutters ALL the time, from start-up to shutdown. Just yesterday it worked fine, in fact I left my computer running till 3 in the morning, and I woke up to shut it down, and the mouse worked fine. This morning however, at the splash screen, the mouse stutters, when I login, the mouse stutters, I've adjusted the settings for the mouse, but they appear to do nothing to fix the problem; I've also tried using the free NVIDIA drivers. I really don't know alot about how Linux works, but everything was working fine for me up until now; I've checked over this forum, and Google, and found no viable solutions for this.

And in retrospect, sorry for the long post. :\ [/rant]

---

### Post by Crafty Kisses on 2008-02-26
That's weird, could be a possible RAM issue, post the following output, and lets see what's running:
```
top
```

---

### Post by hmGIR on 2008-02-26
```
top - 18:39:00 up  1:33,  2 users,  load average: 0.62, 0.81, 0.96
Tasks: 110 total,   2 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0%us,  0.6%sy,  0.1%ni, 89.8%id,  3.3%wa,  1.1%hi,  0.1%si,  0.0%st
Mem:   1001984k total,   694592k used,   307392k free,    41972k buffers
Swap:  2931820k total,        0k used,  2931820k free,   379388k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6146 sean      15   0  188m  69m  22m R    4  7.1   4:44.77 firefox-bin        
 7168 sean      15   0  2360 1076  808 R    2  0.1   0:00.01 top                
    1 root      15   0  2948 1852  532 S    0  0.2   0:01.30 init               
    2 root      19  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1        
    7 root      39  19     0    0    0 S    0  0.0   0:00.15 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.52 events/1           
   11 root      19  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   32 root      10  -5     0    0    0 S    0  0.0   0:02.03 kblockd/1          
   33 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   34 root      14  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  128 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod            
  153 root      16   0     0    0    0 S    0  0.0   0:00.00 pdflush            
  154 root      15   0     0    0    0 S    0  0.0   0:00.09 pdflush            
  155 root      13  -5     0    0    0 S    0  0.0   0:00.00 kswapd0            
  206 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  207 root      14  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 2110 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 2120 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd              
 2152 root      20  -5     0    0    0 S    0  0.0   0:00.00 ata/0              
 2153 root      19  -5     0    0    0 S    0  0.0   0:00.00 ata/1              
 2154 root      19  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
 2298 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
 2299 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1          
 2899 root      10  -5     0    0    0 S    0  0.0   0:01.38 kjournald          
 3126 root      21  -4  3028 1380  408 S    0  0.1   0:00.50 udevd              
 4251 root      12  -5     0    0    0 S    0  0.0   0:00.00 kgameportd         
 4728 root      18   0  1692  516  448 S    0  0.1   0:00.00 getty              
 4729 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty              
 4731 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty              
 4733 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty              
 4735 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty  

```

---

### Post by Therion on 2008-02-26
Watching this thread with interest simply because I have (but don't currently use) a Logitech MX700 (USB) that I like very much, but just won't get along with Ubuntu for this very reason.  It's hard to describe, but "stutter" is a good way to put it.  It's incredibly annoying when it happens.  I never did figure out what was causing it.  I switched to a really cheap little MS optical mouse ($15 or thereabouts and USB as well) and the problem went away.

---

### Post by hmGIR on 2008-02-26
> **Therion said:**
> Watching this thread with interest simply because I have (but don't currently use) a Logitech MX700 (USB) that I like very much, but just won't get along with Ubuntu for this very reason.  It's hard to describe, but "stutter" is a good way to put it.  It's incredibly annoying when it happens.  I never did figure out what was causing it.  I switched to a really cheap little MS optical mouse ($15 or thereabouts and USB as well) and the problem went away.

Problem is, I've tried using a different mouse and get the same results.

---

### Post by Crafty Kisses on 2008-02-26
> **hmGIR said:**
> Problem is, I've tried using a different mouse and get the same results.

That's really werid, and you've tried both USB mouse, and a convential mouse?

---

### Post by hmGIR on 2008-02-26
I've tried two different laser-mice on different USB ports, but no, I haven't tried using a PS/2 mouse. I wouldn't expect it to be a problem with the ports, since it worked fine last night, and I haven't physically moved anything around. Any chance WINE could be the problem? I installed that last night, but the mouse still worked afterwards, only now when I start my system up does it stutter. :\

---

### Post by hmGIR on 2008-02-26
Okay, so I restarted my computer again, and during boot I got this error message constantly:
```
usb 5-7: device did not accept address [several different numbers], error -110
```

Not sure what this means, but it hasn't shown up before this problem.

---

### Post by tgilbert328 on 2008-02-26
This may sound crazy, but I had the identical problem with my mouse.  If I plug the mouse into the front USB ports, its stutters every few seconds and then jumps back to life.

If I plug the mouse into the USB ports on the back of the computer, it doesn't...

Its consistent and I can replicate it.

Tim

---

### Post by hmGIR on 2008-02-26
I had a similar problem like that a while back, and I have tried using the fron USB ports (I'm using it right now, in fact) and I still get the stuttering. :(

---

### Post by Therion on 2008-02-26
> **tgilbert328 said:**
> This may sound crazy, but I had the identical problem with my mouse.  If I plug the mouse into the front USB ports, its stutters every few seconds and then jumps back to life.

If I plug the mouse into the USB ports on the back of the computer, it doesn't...

Its consistent and I can replicate it.

Tim
Just so you know why that may be the case...  Font-panel USB connectors are notorious for not delivering good clean power consistently.  It's usually good enough to get by on, but the rear USB ports connect directly to the motherboard (instead of through usb headers and such like the front mounted ports) so they're almost certain to get a cleaner, more consistent power feed and thus provide more stable connectivity.

Just in case that was keeping you awake at night or something...

---

### Post by hmGIR on 2008-02-26
I AM LIKE UNTO A GOD!

Just kidding, I fixed it. I took out my PCI cards and hard drives, cleaned the case and fans using compressed air, and switched my defective hard drive into slave mode, and my working drive to master w/slave. For some reason, IT WORKED! :D

My mouse is now stutter free, don't know why cleaning it fixed it, since it worked last night, but I'll take what I can get. :p

Thanks for trying to help out, Codename; Therion and Tim, you may just want to try cleaning the case out, crazy, I know, but it might work for you guys too. :p

---

