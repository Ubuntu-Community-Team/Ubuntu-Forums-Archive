---
title: "unusual high system load after upgrade to 15.10 (with new hardware)"
date: 2015-10-29
forum: General Help
---

### Post by odror on 2015-10-29
CPU: i7-5820k
RAM: 32GB
Video: GTX980.

I use SSD as Hard drive.

After booting the system (with almost nothing going on) the system load is around 3.

Gradually throughout the day it increases some time up to 16. Even if the CPU load is low.

I cannot tell what is the issues

top:
```
top - 08:53:17 up  1:33,  4 users,  load average: 2.59, 2.72, 2.87
Tasks: 389 total,   1 running, 387 sleeping,   0 stopped,   1 zombie
%Cpu(s):  3.1 us,  0.7 sy,  0.0 ni, 96.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  32838796 total,  8696072 used, 24142724 free,  1384556 buffers
KiB Swap: 16587772 total,        0 used, 16587772 free.  2563596 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                 
13243 user      20   0  979976 478276  34856 S   9.6  1.5  16:43.31 chrome                                                                                  
13131 user      20   0 1017304 280136  74012 S   8.0  0.9  24:32.36 chrome                                                                                  
30116 user      20   0  878532 142848  73436 S   6.6  0.4   1:06.38 chrome                                                                                  
12862 user      20   0  620240 212492  87908 S   2.7  0.6   1:39.53 chrome                                                                                  
11807 user      20   0  898548  87528  67200 S   2.3  0.3   0:34.71 konsole                                                                                 
12806 user      20   0 1222244 230356 102164 S   2.3  0.7   1:53.77 chrome                                                                                  
 2559 root      20   0 2326096 362984 309156 S   1.3  1.1   3:30.00 Xorg                                                                                    
27976 root      20   0 3738372 539588 104016 S   1.0  1.6   0:14.63 mythtv-setup.re                                                                         
  125 root      20   0       0      0      0 D   0.7  0.0   0:25.08 kworker/5:1                                                                             
12891 user      20   0 1264444 217776  53416 S   0.7  0.7   0:20.38 chrome                                                                                  
30860 user      20   0   25124   3276   2544 R   0.7  0.0   0:01.97 top                                                                                     
    7 root      20   0       0      0      0 S   0.3  0.0   0:06.97 rcu_sched                                                                               
   18 root      20   0       0      0      0 S   0.3  0.0   0:00.70 rcuos/1                                                                                 
  553 root      20   0       0      0      0 S   0.3  0.0   0:00.22 kworker/0:1                                                                             
11120 user      20   0  646540  46712  29924 S   0.3  0.1   0:05.43 grive-indicator                                                                         
11149 user      20   0 1833604 111136  42620 S   0.3  0.3   0:07.89 variety                                                                                 
    1 root      20   0  185732   6380   3916 S   0.0  0.0   0:01.75 systemd                                                                                 
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                                                                                
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.15 ksoftirqd/0                                                                             
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                                                                            
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                                                                                  
    9 root      20   0       0      0      0 S   0.0  0.0   0:03.03 rcuos/0                                                                                 
```

iotop does not show any unusual activity.

Is there a way to find what cause the high system load. 
I search on the web, nothing seems to be applicable.
Can this be a kernel bug??

Any help will be appreciated

---

### Post by sandyd on 2015-10-29
Are any of your partitions full by any chance?

---

### Post by odror on 2015-10-29
I have plenty of space in my partitions.

```
Filesystem      1K-blocks       Used  Available Use% Mounted on
udev             16401552          0   16401552   0% /dev
tmpfs             3283880      11244    3272636   1% /run
/dev/sda2       733147504  424568764  276420108  61% /
tmpfs            16419396      57556   16361840   1% /dev/shm
tmpfs                5120          4       5116   1% /run/lock
tmpfs            16419396          0   16419396   0% /sys/fs/cgroup
/dev/sda1          523248       4708     518540   1% /boot/efi
/dev/sdc4      2757025384 1417388640 1199564860  55% /disk0
cgmfs                 100          0        100   0% /run/cgmanager/fs
tmpfs             3283880         24    3283856   1% /run/user/1000
tmpfs             3283880          8    3283872   1% /run/user/112

```

I have also installed a  new version of 15.10 and I get system load over 2 when there no application running or services being provided.

---

