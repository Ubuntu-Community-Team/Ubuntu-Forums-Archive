---
title: "PC frozen after running out the memory (physical)"
date: 2019-08-28
forum: General Help
---

### Post by jrecuerda on 2019-08-28
Hi,

I am experiencing an issue in Ubuntu 18.04. The PC gets frozen in such a way that I have to press the power button to reboot it when it runs out the physical memory. The thin is that is is using only about 1.6G of the swap memory.

The output of the free command is the following:
```
  
              total        used        free      shared  buff/cache   available
Mem:            15G         13G        217M        103M        2,2G        2,0G
Swap:           31G         20M         31G



```

When the used memory reach almost 14 it gets frozen. Should it do more swapping trying not to become unusable?

The swappiness is set to 60.

Thanks!

---

### Post by crip720 on 2019-08-28
What is using all your memory and how much cpu are you using?

---

### Post by oldfred on 2019-08-28
Its normal for Ubuntu to use all your RAM, most is cache.

       Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649) &
[https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221](https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221) 
    
So is issue then some application or something else?

---

### Post by jrecuerda on 2019-08-29
This is the top command output before becoming unusable, I mean that when I have less than 1G of available memory it is hard to do any simple task like posting this message.

@olfred I think it is not due to caching

```
Tasks: 426 total,   1 running, 316 sleeping,   0 stopped,   0 zombie%Cpu(s):  0,7 us,  0,3 sy,  0,1 ni, 98,7 id,  0,1 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem : 16288640 total,   240244 free, 13827776 used,  2220620 buff/cache
KiB Swap: 33554428 total, 32884728 free,   669700 used.  2023760 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                             
 4739 root      20   0  286920  28712  15072 S   2,7  0,2   7:55.95 Xorg                                
 7936 jesus.r+  20   0  583684  49808  32872 S   2,0  0,3   0:40.88 gnome-system-mo                     
10031 jesus.r+  20   0 17,069g 1,158g  42116 S   2,0  7,5   0:42.65 java                                
 5199 jesus.r+  20   0 4677208 215692  52332 S   1,9  1,3  13:07.62 gnome-shell                         
 5945 jesus.r+  20   0  9,949g 1,080g  23708 S   1,2  7,0  22:51.82 java                                
 5845 jesus.r+  20   0 10,195g 3,910g  19640 S   1,1 25,2  72:10.90 java                                
20603 jesus.r+  25   5  722964  48584  18232 S   1,1  0,3   0:36.11 python2                             
 2552 root     -51   0       0      0      0 S   0,3  0,0   3:58.20 irq/130-nvidia                      
 8897 jesus.r+  20   0 11,253g 2,154g  19456 S   0,3 13,9   4:49.38 java                                
11247 jesus.r+  25   5   51596   4460   3412 R   0,3  0,0   0:04.76 top                                 
11260 jesus.r+  25   5   57076   6828   4340 S   0,3  0,0   0:01.01 zsh                                 
22783 jesus.r+  20   0  814356  98560  28640 S   0,3  0,6   2:24.37 chrome                              
30029 jesus.r+  20   0  851260  33524    804 S   0,3  0,2   2:30.15 python3.6                           
 8520 jesus.r+  20   0 11,517g 1,013g  26312 S   0,2  6,5   1:20.13 java                                
10204 jesus.r+  20   0 7456692  85980  18536 S   0,2  0,5   0:01.80 java                                
10205 jesus.r+  20   0 29,454g 271584 175632 S   0,2  1,7   0:03.06 java                                
10215 jesus.r+  20   0 22,817g 193348 164768 S   0,2  1,2   0:01.32 shapelets-worke                     
19895 jesus.r+  20   0 1432184 227120  64732 S   0,2  1,4  16:55.51 chrome                              
19946 jesus.r+  20   0  590148  79616  21504 S   0,2  0,5   3:01.96 chrome                              
 1474 root      20   0  566164   7460   5212 S   0,1  0,0   0:47.79 NetworkManager                      
 2583 gdm       20   0 4031636  67888  39880 S   0,1  0,4   1:43.32 gnome-shell                         
 6836 root      20   0  556212   4968   2108 S   0,1  0,0   0:02.64 fwupd                               
10207 jesus.r+  20   0 24,169g 296532 215988 S   0,1  1,8   0:03.82 python                              
10209 jesus.r+  20   0 24,169g 297112 216504 S   0,1  1,8   0:03.56 python                              
10211 jesus.r+  20   0 22,817g 194952 166284 S   0,1  1,2   0:01.27 shapelets-worke                     
19937 jesus.r+  20   0  807944 226580  58652 S   0,1  1,4  10:09.04 chrome                              
20741 jesus.r+  20   0 1202456  69440  23232 S   0,1  0,4   1:29.94 electron                            
20821 jesus.r+  20   0 1217724 317952  35372 S   0,1  2,0   4:11.58 electron                            
22423 jesus.r+  20   0  855776 106856  48756 S   0,1  0,7   1:25.82 chrome                              
22457 jesus.r+  20   0  884360 110300  37884 S   0,1  0,7   1:46.11 chrome                              
    1 root      20   0  225932   5612   3460 S   0,0  0,0   1:22.54 systemd                             
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.10 kthreadd                            
    4 root       0 -20       0      0      0 I   0,0  0,0   0:00.00 kworker/0:0H                        
    6 root       0 -20       0      0      0 I   0,0  0,0   0:00.00 mm_percpu_wq                        
    7 root      20   0       0      0      0 S   0,0  0,0   0:00.29 ksoftirqd/0                         
    8 root      20   0       0      0      0 I   0,0  0,0   0:26.22 rcu_sched                           
    9 root      20   0       0      0      0 I   0,0  0,0   0:00.00 rcu_bh                              
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.03 migration/0                         
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.14 watchdog/0                          
   12 root      20   0       0      0      0 S   0,0  0,0   0:00.00 cpuhp/0                
```

---

### Post by CatKiller on 2019-08-29
> **jrecuerda said:**
> When the used memory reach almost 14 it gets frozen. Should it do more swapping trying not to become unusable?
No. Not everything can be put in swap. All computers will react badly to running out of RAM. 

In your case, it appears to be your java application that's causing your problem. Either a memory leak, or misconfigured memory allocation / garbage collection.

---

