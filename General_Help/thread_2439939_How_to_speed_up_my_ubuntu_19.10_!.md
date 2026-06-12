---
title: "How to speed up my ubuntu 19.10 ?!"
date: 2020-04-03
forum: General Help
---

### Post by fairbird on 2020-04-03
My ubuntu 19.10 (4GB Ram)
```
Linux 5.3.0-45-generic #37-Ubuntu SMP Thu Mar 26 20:41:27 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
Before  one week ago works normal. But after that slow motion became sudden.
Not booting issue ... after booting I can not open any things normally ..
For example If I want to open terminal. It will be take few seconds around 6 to 10. Before that just one second take to open it.

I have tried some terminal commands . but nothing change.
How to solve it Please ?!

Thank you

---

### Post by CelticWarrior on 2020-04-03
How much free space do you have in the root partition?

---

### Post by fairbird on 2020-04-03
Thank you for answer ...
I have around (73G)
```
Filesystem      Size  Used Avail Use% Mounted onudev            1.9G     0  1.9G   0% /dev
tmpfs           382M  1.9M  380M   1% /run
/dev/sda7       290G  202G   73G  74% /
tmpfs           1.9G   25M  1.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop0      203M  203M     0 100% /snap/vlc/1049
/dev/loop1       60M   60M     0 100% /snap/easy-disk-cleaner/23
/dev/loop2      1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop4      256K  256K     0 100% /snap/gtk2-common-themes/9
/dev/loop3       94M   94M     0 100% /snap/core/8935
/dev/loop5      157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop6       58M   58M     0 100% /snap/jdownloader2/3
/dev/loop7       95M   95M     0 100% /snap/b2/6
/dev/loop10     4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/loop9       66M   66M     0 100% /snap/uget/1
/dev/loop14      15M   15M     0 100% /snap/gnome-characters/399
/dev/loop18      15M   15M     0 100% /snap/gnome-characters/495
/dev/loop13     102M  102M     0 100% /snap/p7zip-desktop/220
/dev/loop12     161M  161M     0 100% /snap/gnome-3-28-1804/116
/dev/loop19     4.4M  4.4M     0 100% /snap/gnome-calculator/704
/dev/loop23     1.0M  1.0M     0 100% /snap/gnome-logs/93
/dev/loop8      174M  174M     0 100% /snap/gimp/252
/dev/loop17      55M   55M     0 100% /snap/core18/1705
/dev/loop21      60M   60M     0 100% /snap/easy-disk-cleaner/24
/dev/loop11      49M   49M     0 100% /snap/gtk-common-themes/1474
/dev/loop25      92M   92M     0 100% /snap/core/8689
/dev/loop15     256K  256K     0 100% /snap/gtk2-common-themes/5
/dev/loop22     172M  172M     0 100% /snap/gimp/246
/dev/loop20     203M  203M     0 100% /snap/vlc/1397
/dev/loop16      50M   50M     0 100% /snap/ghex-udt/1
/dev/loop24      55M   55M     0 100% /snap/core18/1668
/dev/loop26      45M   45M     0 100% /snap/gtk-common-themes/1440
tmpfs           382M   40K  382M   1% /run/user/1000



```

---

### Post by lvm on 2020-04-03
Start top and monitor what's going on when system slows down paying special attention to cpu, memory and swap lines and programs on top of the list.

---

### Post by fairbird on 2020-04-03
Please have you look on my output of top command ...
```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                  
16940 raed      20   0  366976  25912  21160 R 100.0   0.7   0:31.89 tracker-store                                                                            
    1 root      20   0  170268   9772   7248 S   0.3   0.2   0:08.83 systemd                                                                                  
 1212 raed      20   0  286064  25192  13976 S   0.3   0.6   4:25.11 Xorg                                                                                     
 1594 raed      20   0 3229088 191388  77248 S   0.3   4.9   5:23.56 gnome-shell                                                                              
 1743 raed      20   0  458892   8172   6468 S   0.3   0.2   0:31.04 ibus-daemon                                                                              
15828 root       0 -20       0      0      0 I   0.3   0.0   0:00.40 kworker/u9:2-hci0                                                                        
15831 raed      20   0  777292 252728 165156 S   0.3   6.5   0:27.70 chrome                                                                                   
16874 raed      20   0 4604204  90156  68664 S   0.3   2.3   0:00.38 chrome                                                                                   
16953 raed      20   0  958388  45000  32820 S   0.3   1.2   0:00.77 gnome-terminal-                                                                          
    2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd                                                                                 
    3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                                   
    4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                               
    9 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq                                                                             
   10 root      20   0       0      0      0 S   0.0   0.0   0:00.25 ksoftirqd/0                                                                              
   11 root      20   0       0      0      0 I   0.0   0.0   0:07.73 rcu_sched                                                                                
   12 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/0                                                                              
   13 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                            
   14 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                  
   15 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                  
   16 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                            
   17 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/1                                                                              
   18 root      20   0       0      0      0 S   0.0   0.0   0:00.39 ksoftirqd/1                                                                              
   21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                  
   22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                            
   23 root      rt   0       0      0      0 S   0.0   0.0   0:00.04 migration/2                                                                              
   24 root      20   0       0      0      0 S   0.0   0.0   0:00.18 ksoftirqd/2                                                                              
   27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                  
   28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                            
   29 root      rt   0       0      0      0 S   0.0   0.0   0:00.04 migration/3                                                                              
   30 root      20   0       0      0      0 S   0.0   0.0   0:00.13 ksoftirqd/3                                                                              
   33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kdevtmpfs                                                                                
   34 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns                                                                                    
   35 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_kthre                                                                          
   36 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd                                                                                  
   37 root      20   0       0      0      0 S   0.0   0.0   0:00.01 khungtaskd                                                                               
   38 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper  
```

---

### Post by Yellow Pasque on 2020-04-03
The "tracker-store" process is using a lot of CPU. (tracker-store is a file indexing process.) If it's always using 100% CPU whenever you run htop, you probably need to reset tracker, because of corrupted database or cache info.
```
tracker reset -r
```

---

### Post by fairbird on 2020-04-04
Thank you .. I think I need to reinstall my ubuntu again.

---

### Post by Yellow Pasque on 2020-04-04
> **fairbird said:**
> Thank you .. I think I need to reinstall my ubuntu again.

So.... Did you run the command to reset the tracker DB? Is tracker still consuming 100% CPU?

---

### Post by fairbird on 2020-04-04
Yes... I did it.
And there is a slight difference after applying the command, but it did not completely solve the problem
```
raed@fairbird:~$ tracker reset -rCAUTION: This process may irreversibly delete data.
Although most content indexed by Tracker can be safely reindexed, it can’t be assured that this is the case for all data. Be aware that you may be incurring in a data loss situation, proceed at your own risk.


Are you sure you want to proceed? [y|N]: y
Found 3 PIDs…
  Killed process 1847 — “tracker-extract”
  Killed process 1850 — “tracker-miner-fs”
  Killed process 13170 — “tracker-store”
_g_io_module_get_default: Found default implementation dconf (DConfSettingsBackend) for ‘gsettings-backend’
Setting database locations
Checking database directories exist
Checking database version
Checking whether database files exist
Removing all database/storage files
  Removing database:'/home/raed/.cache/tracker/meta.db'
  Removing db-locale file:'/home/raed/.cache/tracker/db-locale.txt'
  Removing journal:'/home/raed/.local/share/tracker/data/tracker-store.journal'
  Removing db-version file:'/home/raed/.cache/tracker/db-version.txt'

```

```


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                  
 1611 raed      20   0 3155244 211516  81160 S   6.0   5.4   3:17.16 gnome-shell                                                                              
 1223 raed      20   0  283992  26392  13052 S   5.3   0.7   2:26.09 Xorg                                                                                     
13422 raed      20   0  958356  46432  34160 S   4.0   1.2   0:00.87 gnome-terminal-                                                                          
 1533 raed      20   0  162760   4748   4560 S   0.3   0.1   0:01.56 at-spi2-registr                                                                          
 1740 raed      20   0  384924   8232   6268 S   0.3   0.2   0:08.62 ibus-daemon                                                                              
 1751 raed      20   0  273840  17992   7872 S   0.3   0.5   0:03.56 ibus-extension-                                                                          
11226 root      20   0       0      0      0 I   0.3   0.0   0:00.21 kworker/0:3-events                                                                       
12503 raed      20   0  797692 274380 185640 S   0.3   7.0   0:24.94 chrome                                                                                   
12547 raed      20   0  326056  89184  64736 S   0.3   2.3   0:22.83 chrome                                                                                   
    1 root      20   0  169084   8648   6504 S   0.0   0.2   0:05.03 systemd                                                                                  
    2 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kthreadd                                                                                 
    3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                                   
    4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                               
    9 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq                                                                             
   10 root      20   0       0      0      0 S   0.0   0.0   0:00.17 ksoftirqd/0                                                                              
   11 root      20   0       0      0      0 I   0.0   0.0   0:05.70 rcu_sched                                                                                
   12 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/0                                                                              
   13 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                            
   14 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                  
   15 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                  
   16 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                            
   17 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/1                                                                              
   18 root      20   0       0      0      0 S   0.0   0.0   0:00.32 ksoftirqd/1                                                                              
   21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                  
   22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                            
   23 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/2                                                                              
   24 root      20   0       0      0      0 S   0.0   0.0   0:00.16 ksoftirqd/2                                                                              
   27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                  
   28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                            
   29 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/3                                                                              
   30 root      20   0       0      0      0 S   0.0   0.0   0:00.14 ksoftirqd/3                                                                              
   33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kdevtmpfs                                                                                
   34 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns                                                                                    
   35 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_kthre                                                                          
   36 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd                                                                                  
   37 root      20   0       0      0      0 S   0.0   0.0   0:00.01 khungtaskd 
```

Thank you

---

