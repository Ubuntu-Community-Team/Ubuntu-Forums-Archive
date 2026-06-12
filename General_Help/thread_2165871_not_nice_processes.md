---
title: "not nice processes"
date: 2013-08-06
forum: General Help
---

### Post by conradin on 2013-08-06
I am looking at some of the not very nice processes on my computer. 
I have some one doing calculations, so things are running peak anyhow, which got me into looking.
looking at the processes running at -20 nice, I wonder what the heck some of them are.
like what are: md, devfreq_wq, khelper, kworker/1:0H,
etc. in fact what does kworker/1:0H even mean?  
Things like cpuset, i see the man page for, but I still dont know if it should run at -20 nice.
Does anyone see anything amiss here? 


```

                                                                        
                                                                         
14420 user2    10 -10  4500 1192  776 R  96.1  0.0   1764:14 stock2011.bin                                                                                    
14434 user2    20   0  4500 1192  776 R  96.1  0.0   1700:20 stock2011.bin                                                                                    
29720 user       20   0 1243m 799m  26m R  96.1 20.2  69:42.30 plugin-containe                                                                                  
15792 user2    20   0  4500 1192  776 R  83.3  0.0   1135:04 stock4000.bin                                                                                    
14340 user2    20   0  4508 1192  776 R  12.8  0.0   1726:27 stock2011.bin                                                                                    
29671 user       20   0 1035m 389m  41m R  12.8  9.8   9:24.61 firefox                                                                                          
    1 root      20   0  4016 2400 1408 S   0.0  0.1   0:02.70 init                                                                                             
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd                                                                                         
    3 root      20   0     0    0    0 S   0.0  0.0   0:01.06 ksoftirqd/0                                                                                      
    5 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0H                                                                                     
    6 root      20   0     0    0    0 S   0.0  0.0   0:00.41 kworker/u:0                                                                                      
    7 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/u:0H                                                                                     
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.20 migration/0                                                                                      
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcu_bh                                                                                           
   10 root      20   0     0    0    0 S   0.0  0.0   0:02.20 rcu_sched                                                                                        
   11 root      rt   0     0    0    0 S   0.0  0.0   0:00.31 watchdog/0                                                                                       
   12 root      rt   0     0    0    0 S   0.0  0.0   0:00.29 watchdog/1                                                                                       
   13 root      20   0     0    0    0 S   0.0  0.0   0:00.74 ksoftirqd/1                                                                                      
   14 root      rt   0     0    0    0 S   0.0  0.0   0:00.16 migration/1                                                                                      
   15 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/1:0                                                                                      
   16 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/1:0H                                                                                     
   17 root      rt   0     0    0    0 S   0.0  0.0   0:00.27 watchdog/2                                                                                       
   18 root      20   0     0    0    0 S   0.0  0.0   0:00.68 ksoftirqd/2                                                                                      
   19 root      rt   0     0    0    0 S   0.0  0.0   0:00.20 migration/2                                                                                      
   21 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/2:0H                                                                                     
   22 root      rt   0     0    0    0 S   0.0  0.0   0:00.26 watchdog/3                                                                                       
   23 root      20   0     0    0    0 S   0.0  0.0   0:00.54 ksoftirqd/3                                                                                      
   24 root      rt   0     0    0    0 S   0.0  0.0   0:00.16 migration/3                                                                                      
   26 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/3:0H                                                                                     
   27 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cpuset                                                                                           
   28 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper                                                                                          
   29 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs                                                                                        
   30 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 netns                                                                                            
   31 root      20   0     0    0    0 S   0.0  0.0   0:00.00 bdi-default                                                                                      
   32 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kintegrityd                                                                                      
   33 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kblockd                                                                                          
   34 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 ata_sff                                                                                          
   35 root      20   0     0    0    0 S   0.0  0.0   0:00.00 khubd                                                                                            
   36 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 md                                                                                               
   37 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 devfreq_wq                                                                                       
   38 root      20   0     0    0    0 S   0.0  0.0   0:32.40 kworker/0:1                                                                                      
   40 root      20   0     0    0    0 R   0.0  0.0   0:35.90 kworker/2:1                                                                                      
   41 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/3:1                                                                                      
   42 root      20   0     0    0    0 S   0.0  0.0   0:00.03 khungtaskd                                                                                       
   43 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kswapd0                                                                                          
   44 root      25   5     0    0    0 S   0.0  0.0   0:00.00 ksmd                                                                                             
   45 root      39  19     0    0    0 S   0.0  0.0   0:00.00 khugepaged                                                                                       
   46 root      20   0     0    0    0 S   0.0  0.0   0:00.00 fsnotify_mark

```

---

### Post by Cheesemill on 2013-08-06
khelper and kworker are kernel processes, you don't want to change the nice value of these as they are partly responsible for the smooth running of all the other processes.

Generally you shouldn't change the nice value of anything on your system as the kernel does a good job of allocating resources by itself, this is especially true of system processes.

---

