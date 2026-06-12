---
title: "RAM use doubles over time..."
date: 2014-05-13
forum: General Help
---

### Post by timgood on 2014-05-13
I don't know if this is usual, but when I reboot Kubuntu 14.04 64bit, my RAM usage (as monitored by conky) starts off at around 10%. Over the course of two days it will gradually go up to around 20% and often after this the system becomes unresponsive. I have checked my RAM and it is all good. Any idea how I can find out what is causing this? Thanks guys.

---

### Post by mastablasta on 2014-05-13
it is nothing unusual if RAM is used (that's why it's there for).

the unresponsiveness is more unusual though. did you notice any processes taking up the CPU?

how much RAM do you have in total?

---

### Post by timgood on 2014-05-13
I have 12GB RAM - looking at top I can't see any processes that are taking up the RAM. It's more like the RAM is not released after programs are closed down. Conky showing RAM use at 12% after 5 hours of up-time. Top gives me:

1564 root      20   0  203548  84196  48508 S   3.3  0.7  46:27.46 Xorg                                     
 2594 tim       20   0  528824 176652  45220 S   2.3  1.4   7:52.44 skype                                    
13115 tim       20   0  516916  29596  19976 S   2.0  0.2   0:00.54 konsole                                  
 2634 tim       20   0  526184  54036   8980 S   1.3  0.4   4:23.90 conky                                    
 1181 root      20   0    4368    688    516 S   1.0  0.0   0:11.84 acpid                                    
13055 tim       20   0  991504  83596  24708 S   1.0  0.7   0:02.70 chrome                                   1564 root      20   0  203548  84196  48508 S   3.3  0.7  46:27.46 Xorg                                     
 2594 tim       20   0  528824 176652  45220 S   2.3  1.4   7:52.44 skype                                    
13115 tim       20   0  516916  29596  19976 S   2.0  0.2   0:00.54 konsole                                  
 2634 tim       20   0  526184  54036   8980 S   1.3  0.4   4:23.90 conky                                    
 1181 root      20   0    4368    688    516 S   1.0  0.0   0:11.84 acpid                                    
13055 tim       20   0  991504  83596  24708 S   1.0  0.7   0:02.70 chrome                                   
 2610 tim       20   0 1232764 139428  53816 S   0.7  1.1   2:33.73 chrome                                   
   30 root      20   0       0      0      0 S   0.3  0.0   0:04.08 kworker/1:0                              
 2859 tim       20   0 1107344 132600  39492 S   0.3  1.1   1:01.22 chrome                                   
12737 tim       20   0 1195528 201344  34560 S   0.3  1.6   0:20.90 chrome                                   
13140 tim       20   0   24988   1776   1212 R   0.3  0.0   0:00.06 top                                      
    1 root      20   0   33920   3232   1500 S   0.0  0.0   0:01.53 init                   
 2610 tim       20   0 1232764 139428  53816 S   0.7  1.1   2:33.73 chrome                                   
   30 root      20   0       0      0      0 S   0.3  0.0   0:04.08 kworker/1:0                              
 2859 tim       20   0 1107344 132600  39492 S   0.3  1.1   1:01.22 chrome                                   
12737 tim       20   0 1195528 201344  34560 S   0.3  1.6   0:20.90 chrome                                   
13140 tim       20   0   24988   1776   1212 R   0.3  0.0   0:00.06 top                                      
    1 root      20   0   33920   3232   1500 S   0.0  0.0   0:01.53 init

Have no idea why chrome appears multiple times? (EDIT) found chrome was running in background. Unticked box and RAM has dropped to 10% again.

---

### Post by oldrocker99 on 2014-05-13
Chrome is kind of a memory hog, which is why Firefox is the default browser in Ubuntu; it was Canonical's decision.

---

### Post by mcduck on 2014-05-13
> **timgood said:**
> I don't know if this is usual, but when I reboot Kubuntu 14.04 64bit, my RAM usage (as monitored by conky) starts off at around 10%. Over the course of two days it will gradually go up to around 20% and often after this the system becomes unresponsive. I have checked my RAM and it is all good. Any idea how I can find out what is causing this? Thanks guys.

Your problem is definitely something else than the RAM usage.

Free RAM doesn't improve performance in any way, and RAM usage only causes issues when it's closet to 100% and there isn't enough RAM available for the processes. With 80% of RAM unused you most certainly are not there yet. :D

I'd recommend taking a better look at running processes and CPU usage instead.

---

### Post by SeijiSensei on 2014-05-13
Remember, too, that Linux uses available memory to cache disk operations.  On the machine I'm typing on, top reports that 7.7 out of 8.1 GB are in use, but 3.4 GB of that is disk cache.  That figure adjusts dynamically depending on the memory demands of the currently-running applications.

---

