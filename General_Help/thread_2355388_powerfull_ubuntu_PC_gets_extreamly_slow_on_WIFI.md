---
title: "powerfull ubuntu PC gets extreamly slow on WIFI"
date: 2017-03-12
forum: General Help
---

### Post by ranma1988 on 2017-03-12
Hi

First of all I have tried (and failed) to find out solution to my poroblem (probably due to bad description).
Im using ubuntu 16.10 on powerfull PC for over 1y and nothing like this has happend before.

My ubuntu is getting extremely slow after connectiong to one particular WIFI network.
Slow but no load is visible in system monitor.
Ex: I have to wait >5sec to see output of any command like $ls $htop etc GUI is getting unresponsive
This was not the case before and after disconnecting from that network or my android as hot spot problem is gone! ubuntu is back to normal speed.

Does any of you know what could be the problem?

---

### Post by HermanAB on 2017-03-12
Open a terminal and run the command top.

The connect to the problem site again and see what happens.

There is also ntop.

---

### Post by ranma1988 on 2017-03-12
Hi HermanAB,
nothing interesting,
I have started $ top and connected to AP WIFI thats causing this issue, sadly there is nothing interesting (note commands still take >5sec to starts)

Tasks: 313 total,   1 running, 312 sleeping,   0 stopped,   0 zombie%Cpu(s):  3,9 us,  1,0 sy,  0,0 ni, 94,7 id,  0,4 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem : 16388684 total,  9784304 free,  2859532 used,  3744848 buff/cache
KiB Swap: 16732156 total, 16732156 free,        0 used. 13034076 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                 
 1900 root      20   0  178020  52904  34384 S   9,3  0,3   4:49.13 Xorg                                                                    
 2189 me     20   0 2313020 524148  89624 S   5,6  3,2   5:57.88 gnome-shell                                                             
 2414 me     20   0 1549420 336000 128032 S   5,0  2,1   7:21.50 chrome                                                                  
 2748 me     20   0 1170296 333400  83672 S   4,3  2,0   2:30.01 chrome                                                                  
 6273 me     20   0  680652  53600  35448 S   4,0  0,3   1:23.11 gnome-system-mo                                                         
10044 me     20   0  769172  73576  54428 S   3,3  0,4   0:00.10 chrome                                                                  
 1844 me     20   0  652972  42000  30116 S   2,7  0,3   2:03.88 gedit                                                                   
 2491 me     20   0  764428 251128  93648 S   2,7  1,5   4:52.49 chrome                                                                  
 1775 gdm       20   0 1499932 148460  80984 S   0,7  0,9   0:17.40 gnome-shell                                                             
 2025 me     20   0  422452   9996   5336 S   0,7  0,1   0:07.66 ibus-daemon                                                             
 2169 me      9 -11  511804  13084   9576 S   0,7  0,1   1:07.80 pulseaudio                                                              
 4632 me     20   0  657660  41792  28912 S   0,7  0,3   0:21.26 gnome-terminal-                                                         
    7 root      20   0       0      0      0 S   0,3  0,0   0:27.65 rcu_sched                                                               
 1654 root     -51   0       0      0      0 S   0,3  0,0   0:48.81 irq/32-nvidia                                                           
 2544 me     20   0 1054004 179188  55696 S   0,3  1,1   0:11.28 chrome                                                                  
 2790 me     20   0 1121668 264424 141828 S   0,3  1,6   2:27.26 chrome                                                                  
 7114 me     20   0 1295168  90656  68640 S   0,3  0,6   0:23.35 gnome-control-c                                                         
 9762 me     20   0   44516   4324   3432 R   0,3  0,0   0:00.20 top   


I am seriously interesded where/what is the problem, why does this AP impact my local program start time...

my wifi-card: 04:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)

---

