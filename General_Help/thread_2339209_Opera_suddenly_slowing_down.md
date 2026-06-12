---
title: "Opera suddenly slowing down"
date: 2016-10-05
forum: General Help
---

### Post by dkolars on 2016-10-05
Running 14.04 64bit...  everything was working fine until last week, when suddenly Opera browser started slowing down, big time...  So, checked memory, and Swap was not being used.  Futzed with that, and was better for a bit, but this week, now I get "Out of memory" errors from all open tabs.  So, edited fstab, # in front of Swap (sda3) line, and restarted.  Of course, no swap file there, and behavior was just as bad.  Manually started swap file, and suddenly all is running smoothly again, swap file being used.

Tonight, slow-down happened again, so checked to find this:



>                total          used           free           shared        buffers     cached
Mem:      16334144   15004596   1329548    8841568     101740    9446364
-/+ buffers/cache:      5456492   10877652
Swap:     16675836    2773636   13902200


Looks like everything is running as it should, but why would a program freeze or slow down for NAR (no apparent reason) after running flawlessly for months?

???

---

### Post by QIII on 2016-10-05
Hello!

Could you start top in the terminal

```
top
```

and do what you have been doing.

When you reach a point where the behavior you are discussing occurs, copy the output of top and post it back here between code tags.

---

### Post by dkolars on 2016-10-07
Since I posted, everything has been working just fine, of course...  but, gone for a few hours tonight and when I came home see that Opera has stopped with:
PAGE CRASHED:  Unfortunately, something caused this page to quit.  It might have been an extensions conflict or some other reason.  Try reloading the page, or navigate to another page to continue.  
But, only one tab crashed, 2 others were fine.

So, looked at top and here's what it has.

> top - 23:12:53 up 2 days,  4:44,  3 users,  load average: 0.00, 0.03, 0.05
Tasks: 271 total,   1 running, 270 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.0 us,  1.0 sy,  0.0 ni, 98.0 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16334144 total, 13372876 used,  2961268 free,    77988 buffers
KiB Swap: 16675836 total,  3495732 used, 13180104 free.  8514804 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                           
 1466 root      20   0  317344 115100  36224 S   7.6  0.7  89:38.08 Xorg                                              
 6125 dk        20   0  771992  15368  11064 S   1.7  0.1   0:25.24 xfce4-terminal                                    
   12 root      20   0       0      0      0 S   0.3  0.0   2:08.75 rcuos/4                                           
  179 root      20   0       0      0      0 S   0.3  0.0   0:11.46 usb-storage                                       
 1279 root      20   0       0      0      0 S   0.3  0.0   0:36.16 kworker/4:1                                       
 2208 dk        20   0  377236  18668   2712 S   0.3  0.1   2:58.55 ibus-daemon                                       
 2344 dk        20   0  741264  17884  11276 S   0.3  0.1   9:25.78 xfce4-panel                                       
 2875 dk        20   0 1768148 420156  47384 S   0.3  2.6 158:22.17 opera                                             
 6145 dk        20   0   32268   1768   1168 R   0.3  0.0   2:02.64 top                                               
 6411 dk        20   0  560756  89364  19192 S   0.3  0.5   8:58.86 opera                                             
 9913 dk        20   0 1302940 302184  71068 S   0.3  1.9  19:57.82 opera                                             
28722 root      20   0       0      0      0 S   0.3  0.0   0:41.97 kworker/1:2                                       
    1 root      20   0   33876   2932   1232 S   0.0  0.0   0:01.67 init                                              
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.04 kthreadd                                          
    3 root      20   0       0      0      0 S   0.0  0.0   0:03.60 ksoftirqd/0                                       
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                                      
    7 root      20   0       0      0      0 S   0.0  0.0   4:08.56 rcu_sched                                         
    8 root      20   0       0      0      0 S   0.0  0.0   2:02.33 rcuos/0                                           
    9 root      20   0       0      0      0 S   0.0  0.0   1:08.23 rcuos/1                                           
   10 root      20   0       0      0      0 S   0.0  0.0   1:55.51 rcuos/2                                           
   11 root      20   0       0      0      0 S   0.0  0.0   1:08.46 rcuos/3                                           
   13 root      20   0       0      0      0 S   0.0  0.0   1:08.32 rcuos/5                                           
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                                            
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0                                           
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1                                           
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2                                           
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3                                           
   19 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/4                                           
   20 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/5                                           
   21 root      rt   0       0      0      0 S   0.0  0.0   0:01.90 migration/0                                       
   22 root      rt   0       0      0      0 S   0.0  0.0   0:00.84 watchdog/0                                        
   23 root      rt   0       0      0      0 S   0.0  0.0   0:00.74 watchdog/1                                        
   24 root      rt   0       0      0      0 S   0.0  0.0   0:01.22 migration/1                                       
   25 root      20   0       0      0      0 S   0.0  0.0   0:05.36 ksoftirqd/1                                       
   27 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H                                      
   28 root      rt   0       0      0      0 S   0.0  0.0   0:00.75 watchdog/2


---

### Post by dkolars on 2016-10-17
Still doing it...  when it happens, the CPU usage by Opera goes to over 100%??!!  So, attached a couple of screen shots of the "top" output...

The 103% happened when scrolling down the Facebook page.  The 115% happened when clicking on a video on Facebook page.  While the video is playing, CPU usage is in the 45-80% range, then drops back to 8-20% when playback is done.   

Using the History Eraser add-on for Opera or BleachBit sometimes improves performance, but no guarantee that they will...  sometimes they barely run.

Closing Opera and re-starting usually works, for a while, but then it starts all over again.  Seems to be mostly browser-related?  Thunderbird works as usual, other programs seem to also work well... of course, when Opera is tying up all the CPU, sometimes nothing works...  other times, I can use other programs.   Sigh.

---

