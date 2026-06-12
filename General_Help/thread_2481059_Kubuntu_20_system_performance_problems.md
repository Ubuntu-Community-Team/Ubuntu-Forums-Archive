---
title: "Kubuntu 20 system performance problems"
date: 2022-11-17
forum: General Help
---

### Post by nilovsergey on 2022-11-17
working in Kubuntu 20 I periodically have big problems with performance : my system practically 
stops and I have to waite for some period to resume my work:
More details about my Laptop and OS :


Running top command I see :


    ```
top - 09:36:02 up  1:20,  1 user,  load average: 9.90, 12.13, 9.24
    Tasks: 281 total,   3 running, 278 sleeping,   0 stopped,   0 zombie
    %Cpu(s): 54.1 us,  2.6 sy,  0.1 ni, 42.6 id,  0.6 wa,  0.0 hi,  0.0 si,  0.0 st
    MiB Mem :   7868.7 total,    695.2 free,   6537.1 used,    636.4 buff/cache
    MiB Swap:   2055.2 total,    123.8 free,   1931.4 used.   1023.8 avail Mem 
    
        PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                    
       4645 postgres  20   0 2870868   2.0g      4 S 100.0  26.5  77:46.78 kswapd0                                                                                                                                    
       4634 master    20   0 2936404   2.0g      4 S  99.3  26.5  77:03.22 kswapd0                                                                                                                                    
       1413 root      20   0  394084  54188  24784 R   6.3   0.7   3:45.59 Xorg                                                                                                                                       
       4259 master    20   0 2897444  60544  47876 R   5.6   0.8   5:04.03 kwin_x11                                                                                                                                   
       4386 master    20   0  357376  39256  25736 S   5.6   0.5   0:16.73 konsole                                                                                                                                    
      13146 master    20   0    7216   5700   3496 S   4.0   0.1   0:01.27 htop                                                                                                                                       
       4303 master    20   0  698316  11784   3332 S   2.0   0.1   1:55.60 audacious                                                                                                                                  
       1461 mysql     20   0 2718356  30808      0 S   0.7   0.4   0:47.92 mysqld                                                                                                                                     
       4008 master     9 -11 1412560   4856   3308 S   0.7   0.1   2:15.42 pulseaudio                                                                                                                                 
       4010 master    39  19  599640  18312   2252 S   0.7   0.2   0:58.10 tracker-miner-f                                                                                                                            
       4325 master    20   0  757580  12072   5012 S   0.7   0.1   0:28.28 ktorrent                                                                                                                                   
       5052 mongodb   20   0 2655964  33524      0 S   0.7   0.4   1:28.78 mongod                                                                                                                                     
         28 root      20   0       0      0      0 S   0.3   0.0   0:02.04 ksoftirqd/2                                                                                                                                
       1527 root     -51   0       0      0      0 S   0.3   0.0   0:42.88 irq/43-nvidia                                                                                                                              
       5209 master    20   0 6818108   1.3g     28 S   0.3  16.4  12:14.31 java                                                                                                                                       
      12347 master    20   0   17016    948      0 R   0.3   0.0   0:01.06 top                                                                                                                                        
      13127 root      20   0       0      0      0 I   0.3   0.0   0:00.04 kworker/1:3-events                                                                                                                         
          1 root      20   0  170908   8460   3708 S   0.0   0.1   0:03.72 systemd                                                                                                                                    
          2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd                                                                                                                                   
          3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp                                                                                                                                     
          4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp                                                                                                                                 
          5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns         
          


```
      
I have worked with postgres priorly, but I removed all postgres packages
from my OS and now I have :

```

    $ apt list --installed  postgres
    Listing... Done
    ...
    $ dpkg -s   postgres
    dpkg-query: package 'postgres' is not installed and no information is available
    Use dpkg --info (= dpkg-deb --info) to examine archive files.



```      




So it is very strange to see postgres in listing of &#8220;top&#8221; coomand
&#8220;master&#8221; - that is name of current user
      
any ideas why so and how that can be fixed?  


    
I have MSI GP70-2PE (GP702PE-426XUA) laptop :
[https://prnt.sc/keAH_wqF18tV](https://prnt.sc/keAH_wqF18tV)
[https://prnt.sc/uCm6oUaZLDbL](https://prnt.sc/uCm6oUaZLDbL)


    ```
$  uname -a
    Linux master-at-home 5.15.0-41-generic #44~20.04.1-Ubuntu SMP Fri Jun 24 13:27:29 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
    
    $ lsb_release -d; uname -r; uname -i
    Description:    Ubuntu 20.04.4 LTS
    5.15.0-41-generic
    x86_64
    $ free
                  total        used        free      shared  buff/cache   available
    Mem:        8059236     6636260      196608      130344     1226368      998828
    Swap:       2104476     1917244      187232
    
    $  kf5-config --version
    Qt: 5.12.8
    KDE Frameworks: 5.68.0
    kf5-config: 1.0

```

Thanks!

---

### Post by nilovsergey on 2022-11-19
After some tests I see that I have problems with performance(my OS pause for some period like 5-10 seconds)
if in my working Chrome browser(Google Chrome
Version 107.0.5304.110 (Official Build) (64-bit)) I open several tabs.
Checking top command :
```
top - 09:51:45 up  3:14,  1 user,  load average: 7.34, 5.57, 5.23
Tasks: 301 total,   4 running, 297 sleeping,   0 stopped,   0 zombie
%Cpu(s): 61.6 us, 34.9 sy,  0.1 ni,  0.1 id,  1.7 wa,  0.0 hi,  1.6 si,  0.0 st
MiB Mem :   7868.7 total,    100.8 free,   7443.9 used,    324.0 buff/cache
MiB Swap:   2055.2 total,      0.0 free,   2055.2 used.     52.1 avail Mem 
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                    
    105 root      20   0       0      0      0 R  99.7   0.0  10:33.35 kswapd0                                                                                                                                    
   4594 postgres  20   0 2739796   2.0g      4 S  87.7  26.5 189:12.95 kswapd0                                                                                                                                    
   4600 master    20   0 2739796   2.0g      4 S  87.7  26.5 189:12.88 kswapd0                                                                                                                                    
  29923 master    20   0 1130.9g 152848  24240 R  28.2   1.9   0:35.17 chrome                                                                                                                                     
  31225 master    20   0 1129.9g 160792  27048 S  21.0   2.0   0:09.57 chrome                                                                                                                                     
  29466 master    20   0   32.6g 151208   9024 S  16.5   1.9   1:13.49 chrome                                                                                                                                     
   4228 master    20   0 2885688  39104  27792 S  11.3   0.5   9:50.37 kwin_x11                                                                                                                                   
  29509 master    20   0   32.6g 137592  33136 R  10.7   1.7   0:20.30 chrome                                                                                                                                     
   1451 root      20   0  393956  60220  32332 S   3.9   0.7   8:50.10 Xorg                                                                                                                                       
  29510 master    20   0   32.3g  33116  15532 S   2.9   0.4   0:07.57 chrome                                                                                                                                     
   4281 master    20   0  698440   8644   2088 S   2.6   0.1   3:26.09 audacious                                                                                                                                  
  29898 master    20   0 1129.9g 104228   4544 S   2.6   1.3   0:19.10 chrome                                                                                                                                     
   4350 master    20   0  680040   5704    452 S   2.3   0.1   0:34.55 ktorrent                                                                                                                                   
   1743 root     -51   0       0      0      0 S   1.3   0.0   1:16.11 irq/43-nvidia                                                                                                                              
  25729 master    20   0 6727456   1.2g     60 S   1.3  15.5  14:08.12 java                                                                                                                                       
   1456 mysql     20   0 2751124  36824      0 S   1.0   0.5   1:40.25 mysqld                                                                                                                                     
   3993 master     9 -11 1412560   3264   1996 S   1.0   0.0   2:03.77 pulseaudio                                                                                                                                 
   3995 master    39  19  679268  12188      0 S   1.0   0.2   1:29.31 tracker-miner-f                                                                                                                            
  29637 master    20   0 1129.9g 117124   8056 S   1.0   1.5   0:09.85 chrome                                                                                                                                     
  29660 master    20   0 1130.9g  58800   1804 S   1.0   0.7   0:05.92 chrome                                                                                                                                     
   7909 master    20   0  353096  14120   7556 S   0.6   0.2   0:13.65 konsole                                                                                                                                    
  29797 master    20   0 1129.9g  25512   1452 S   0.6   0.3   0:01.54 chrome                                                                                                                                     
  29950 master    20   0 1129.9g  93136  14672 S   0.6   1.2   0:16.82 chrome                                                                                                                                     
  31328 master    20   0 1129.9g  40128   5364 S   0.6   0.5   0:01.70 chrome                                                                                                                                     
    116 root       0 -20       0      0      0 I   0.3   0.0   0:04.68 kworker/3:1H-kblockd                                                                                                                       
   1062 root      20   0   90708  16944      0 S   0.3   0.2   1:00.03 mount.ntfs-3g                                                                                                                              
   1318 root      20   0  263956    500      4 S   0.3   0.0   0:01.47 php-fpm8.1                                                                                                                                 
   1336 root      20   0 1495748   5960      0 S   0.3   0.1   0:08.47 containerd                                                                                                                                 
   4231 master    39  19  256.2g    992      0 S   0.3   0.0   0:02.30 baloo_file                                                                                                                                 
   4519 master    20   0  324384   1256      0 S   0.3   0.0   0:01.45 http.so                                                                                                                                    
  29464 root      20   0       0      0      0 I   0.3   0.0   0:01.22 kworker/2:2-events                                                                                                                         
  29538 master    20   0 1129.9g  19256   3312 S   0.3   0.2   0:00.47 chrome                                                                                                                                     
  29935 master    20   0 1129.9g  91480   4348 S   0.3   1.1   0:12.91 chrome                                                                                                                                     
  30655 root      20   0       0      0      0 I   0.3   0.0   0:00.57 kworker/0:0-events                                                                                                                         
  30750 master    20   0 1130.9g  68496   5088 S   0.3   0.9   0:05.18 chrome                                                                                                                                     
  31357 master    20   0   17000   1644    708 R   0.3   0.0   0:00.08 top                                                                                                                                        
      1 root      20   0  169504   1852    144 S   0.0   0.0   0:03.67 systemd                                                                                                                                    
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kthreadd     

```
I see several rows with &#8220;chrome&#8221;, but most of memory takes by 
root,  postgres, master - in first 3 lines and I do not know how can I fix it ?

---

### Post by nilovsergey on 2022-11-19
I tried to delete postgres user in command line, but I got error :
```

sudo deluser  postgres
Removing user `postgres' ...
Warning: group `postgres' has no more members.
userdel: user postgres is currently used by process 3976
/usr/sbin/deluser: `/sbin/userdel postgres' returned error code 8. Exiting.

```
How can I do it ?

---

### Post by deadflowr on 2022-11-19
When posting terminal output please use code tags instead of quote tags.
Code tags will retain the proper formatting and make it easier for users to help.
See:[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")
for a good primer about how use code tags.

While it's understandable wanting to use quotes as it's what is readily available in the quick reply posting option.
They can utterly obliterate the formatting, making reading the output unbearably hard to comprehend.

Not your fault.
Forums can be wacky like that.

---

