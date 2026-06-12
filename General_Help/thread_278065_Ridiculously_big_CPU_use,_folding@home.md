---
title: "Ridiculously big CPU use, folding@home"
date: 2006-10-15
forum: General Help
---

### Post by Anonii on 2006-10-15
Greetings,

this is my top output:

```
top - 00:51:43 up  8:22,  4 users,  load average: 1.53, 1.39, 1.53
Tasks: 110 total,   2 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.8%us,  0.5%sy, 48.5%ni, 46.7%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   1035372k total,  1010508k used,    24864k free,    17252k buffers
Swap:  3028212k total,    17676k used,  3010536k free,   637988k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                         
** 5438 user      39  19 69684  54m 1384 R   97  5.4 472:49.62 FahCore_78.exe                                                                 ** 
 4862 user      15   0  124m  36m  18m S    7  3.6  23:42.21 rhythmbox                                                                       
 4610 user      17   0  4460 1520 1100 S    1  0.1   5:15.87 conky                                                                           
 4054 root      15   0  325m  46m  10m S    1  4.6  31:25.89 Xorg                                                                            
 5273 user      15   0 52676  18m  10m S    1  1.8   0:19.67 gnome-terminal                                                                  
28523 user      16   0 44204  17m  11m S    0  1.8   0:02.38 gaim                                                                            
    1 root      16   0  1628  536  448 S    0  0.1   0:01.03 init                                                                            
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                     
    3 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0                                                                     
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                      
    5 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/1                                                                     
    6 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/1                                                                     
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                      
    8 root      10  -5     0    0    0 S    0  0.0   0:00.46 events/0                                                                        
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                         
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthread                                                                         
   14 root      10  -5     0    0    0 S    0  0.0   0:00.08 kblockd/0                                                                       
   15 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                       
   16 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                          
   17 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                    
  102 root      11  -5     0    0    0 S    0  0.0   0:00.12 kseriod                                                                         
  141 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                         
  142 root      15   0     0    0    0 S    0  0.0   0:00.71 pdflush                                                                         
  143 root      15   0     0    0    0 S    0  0.0   0:01.56 kswapd0                                                                         
  144 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                           
  145 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                           
  773 root      15   0     0    0    0 S    0  0.0   0:00.01 kirqd                                                                           
 1736 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                           
 1819 root      10  -5     0    0    0 S    0  0.0   0:01.47 kjournald                                                                       
 1899 root      15   0  1604  544  468 S    0  0.1   0:00.00 logd                                                                            
 2045 root      12  -4  2616 1048  360 S    0  0.1   0:00.30 udevd                                                                           
 2767 root      13  -5     0    0    0 S    0  0.0   0:00.00 shpchpd                                                                         
 2905 root      20  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                       
 2941 root      20  -5     0    0    0 S    0  0.0   0:00.01 kgameportd                                                                      
 3595 root      16   0  1600  504  432 S    0  0.0   0:00.00 getty                                                                           

```

And from what I see, folding@home takes 97% of my CPU. Am I right?
Helping with folding is alright, but not when it uses all that resources.

Any ideas?

---

### Post by jpkotta on 2006-10-15
Ummm...That is the point.  F@H will use all available CPU power.  It runs at a low priority, so if any other program needs CPU cycles, F@H will yeild to that program.  But you will not be helping if you don't run the program, or if it never uses any CPU.  That is simply what it does, uses spare CPU time.  You are *donating* your spare CPU time.

---

### Post by Anonii on 2006-10-15
I see. 

Thanks for clearing it up. As long as it gives the CPU cycles that other programs need, there is no problem.

Thanks.

---

