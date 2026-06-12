---
title: "many bioset processes"
date: 2016-12-26
forum: General Help
---

### Post by marchello_lippi2 on 2016-12-26
Hi all, top -u root shows many "bioset" processes. What is it and how to reduce their quantity (if possible and if safe). It's 16.04.1 LTS. 

```

  PID &#1050;&#1054;&#1056;.   PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                                                         
  950 root      20   0  334980  39688  22972 S   3,3  2,3  31:29.13 Xorg                                                                                                                                                                            
 7864 root      20   0       0      0      0 S   2,3  0,0   0:01.78 kworker/0:1                                                                                                                                                                     
    7 root      20   0       0      0      0 S   0,3  0,0   1:04.36 rcu_sched                                                                                                                                                                       
 6545 root      20   0       0      0      0 S   0,3  0,0   0:03.62 kworker/1:2                                                                                                                                                                     
    1 root      20   0  119864   4116   2740 S   0,0  0,2   0:03.86 systemd                                                                                                                                                                         
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.04 kthreadd                                                                                                                                                                        
    3 root      20   0       0      0      0 S   0,0  0,0   0:01.24 ksoftirqd/0                                                                                                                                                                     
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:0H                                                                                                                                                                    
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh                                                                                                                                                                          
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.18 migration/0                                                                                                                                                                     
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.66 watchdog/0                                                                                                                                                                      
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.65 watchdog/1                                                                                                                                                                      
   12 root      rt   0       0      0      0 S   0,0  0,0   0:00.19 migration/1                                                                                                                                                                     
   13 root      20   0       0      0      0 S   0,0  0,0   0:03.10 ksoftirqd/1                                                                                                                                                                     
   15 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/1:0H                                                                                                                                                                    
   16 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kdevtmpfs                                                                                                                                                                       
   17 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 netns                                                                                                                                                                           
   18 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 perf                                                                                                                                                                            
   19 root      20   0       0      0      0 S   0,0  0,0   0:00.11 khungtaskd                                                                                                                                                                      
   20 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 writeback                                                                                                                                                                       
   21 root      25   5       0      0      0 S   0,0  0,0   0:00.00 ksmd                                                                                                                                                                            
   22 root      39  19       0      0      0 S   0,0  0,0   0:08.99 khugepaged                                                                                                                                                                      
   23 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 crypto                                                                                                                                                                          
   24 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kintegrityd                                                                                                                                                                     
   25 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   26 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kblockd                                                                                                                                                                         
   27 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 ata_sff                                                                                                                                                                         
   28 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 md                                                                                                                                                                              
   29 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 devfreq_wq                                                                                                                                                                      
   34 root      20   0       0      0      0 S   0,0  0,0   0:04.46 kswapd0                                                                                                                                                                         
   35 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 vmstat                                                                                                                                                                          
   36 root      20   0       0      0      0 S   0,0  0,0   0:00.00 fsnotify_mark                                                                                                                                                                   
   37 root      20   0       0      0      0 S   0,0  0,0   0:00.00 ecryptfs-kthrea                                                                                                                                                                 
   53 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kthrotld                                                                                                                                                                        
   54 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 acpi_thermal_pm                                                                                                                                                                 
   55 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   56 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   58 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   59 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   60 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   61 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   62 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   63 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   64 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   65 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   66 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   67 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   68 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   69 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   70 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   71 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   72 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   73 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   74 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   75 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   76 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset                                                                                                                                                                          
   77 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 bioset

```

---

### Post by wad2 on 2017-02-16
What did you find out about this?  I have same problem.

---

### Post by marchello_lippi2 on 2017-02-16
Nothing so far, but it does not bother me so much now.

---

