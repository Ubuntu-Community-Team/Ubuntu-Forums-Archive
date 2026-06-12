---
title: "Dell Latitude D620 slows for no apparent reason"
date: 2013-12-17
forum: General Help
---

### Post by dwjeanes2 on 2013-12-17
I normally run Ubuntu (12.04 LTS) with basically only 4 apps, KVirc, Firefox, a file window and the default media player. The problem is that I often run into a situation where the system slows dramatically, and even closing all apps doesn't help. Often, even after rebooting, just playing a video, with all other apps closed. results in poor video performance, and the workspace switcher is very slow. I do have an Oracle instance running, but it is not used regularly.

The one symptom I have noticed is high disk activity, but I can't determine why.

Is there a system monitor I can run that will help determine what the problem is? I have looked at the process table and can't find anything that seems abnormal.

What I have done:

Turned off backups
Cleared browser cache
Closed each of my apps to see if one is the culprit
Examined the process table for excessive CPU usage

Any advice would be greatly appreciated.

Thanks!

---

### Post by raja.genupula on 2013-12-17
look with** top** command what eating all your memory

---

### Post by dwjeanes2 on 2013-12-17
> **raja.genupula said:**
> look with** top** command what eating all your memory

Thanks! It appears that Firefox is using about 20% of memory, and that is the largest chunk of all.

here is a snapshot of one 30 second interval:

```
top - 06:41:20 up  4:18,  2 users,  load average: 1.06, 1.18, 1.66
Tasks: 208 total,   1 running, 207 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  0.7%sy,  0.0%ni, 97.4%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1015944k total,   908060k used,   107884k free,    35868k buffers
Swap:  1037308k total,   238276k used,   799032k free,   439528k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                       
 4336 david     20   0  154m  22m  15m S    2  2.3   0:14.11 plugin-containe                                                                                               
 4270 david     20   0  589m 174m  40m S    1 17.6   5:04.85 firefox                                                                                                       
 1135 root      20   0 91604  16m 6544 S    0  1.6  14:30.94 Xorg                                                                                                          
 1856 david     20   0  329m  25m  11m S    0  2.6  11:52.30 compiz                                                                                                        
 2345 david     20   0 55560 4616 3644 S    0  0.5   0:06.93 indicator-datet                                                                                               
 2433 root      20   0 17944 9384 1428 S    0  0.9   1:02.89 landscape-clien                                                                                               
 4012 david     20   0  145m  28m  21m S    0  2.9   1:22.38 konsole                                                                                                       
 1682 david     20   0  7156 2756  576 S    0  0.3   0:28.89 dbus-daemon                                                                                                   
 1864 david     20   0  3712  460  404 S    0  0.0   0:15.78 syndaemon                                                                                                     
 2140 david     20   0 81276 2968 2344 S    0  0.3   0:03.83 e-calendar-fact                                                                                               
 2437 landscap  20   0 20864 9680 2044 S    0  1.0   0:24.05 landscape-monit                                                                                               
 1117 root      20   0  3604  480  404 S    0  0.0   0:07.00 irqbalance                                                                                                    
 1498 oracle    20   0  352m 3064 2820 S    0  0.3   0:07.47 oracle                                                                                                        
 1503 oracle    20   0  351m 3704 3604 S    0  0.4   0:01.49 oracle                                                                                                        
 1565 oracle    20   0  353m  17m  16m S    0  1.8   0:11.85 oracle                                                                                                        
 1734 david     20   0  143m 7440 5000 S    0  0.7   0:15.37 gnome-settings-                                                                                               
 2237 root      20   0 17756  724  596 S    0  0.1   0:00.09 winbindd                                                                                                      
 2436 landscap  20   0 35316  12m 3052 S    0  1.2   0:33.59 landscape-broke                                                                                               
 2438 root      20   0 20836 9.8m 2000 S    0  1.0   0:17.21 landscape-manag                                                                                               
 4213 root      20   0     0    0    0 S    0  0.0   0:12.55 kworker/1:1                                                                                                   
 4268 root      20   0     0    0    0 S    0  0.0   0:05.47 kworker/0:1                                                                                                   
 4362 david     20   0  2852 1192  872 R    0  0.1   0:00.40 top                                                                                                           
 4363 root      20   0     0    0    0 S    0  0.0   0:00.04 kworker/0:2                                                                                                   
    1 root      20   0  3648 1152  660 S    0  0.1   0:04.34 init                                                                                                          
    2 root      20   0     0    0    0 S    0  0.0   0:00.02 kthreadd                                                                                                      
    3 root      20   0     0    0    0 S    0  0.0   0:02.61 ksoftirqd/0                                                                                                   
    5 root      20   0     0    0    0 S    0  0.0   0:04.95 kworker/u:0                                                                                                   
    6 root      RT   0     0    0    0 S    0  0.0   0:01.42 migration/0                                                                                                   
    7 root      RT   0     0    0    0 S    0  0.0   0:00.36 watchdog/0                                                                                                    
    8 root      RT   0     0    0    0 S    0  0.0   0:00.93 migration/1                                                                                                   
   10 root      20   0     0    0    0 S    0  0.0   0:01.56 ksoftirqd/1                                                                                                   
   12 root      RT   0     0    0    0 S    0  0.0   0:00.39 watchdog/1                                                                                                    
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                        
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                       
   15 root      20   0     0    0    0 S    0  0.0   0:00.05 kdevtmpfs                                                                                                     
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                                         
   18 root      20   0     0    0    0 S    0  0.0   0:00.23 sync_supers                                                                                                   
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                                   
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd       

```
any ideas on how to proceed? note that KVirc and media player are not running, it looks like the likely culprit is firefox...

thanks for the help!

---

### Post by J_Me on 2013-12-17
Your system is using 'swap' space so that would explain the disk activity.It's best to have swap installed on the fastest part of a hard drive. Could you run```
sudo fdisk -l
``` from a terminal and post it here.

---

### Post by dwjeanes2 on 2013-12-17
```
david@david-Latitude-D620:~$ sudo fdisk -l
[sudo] password for david: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f1a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   115132415    57565184   83  Linux
/dev/sda2       115134462   117209087     1037313    5  Extended
/dev/sda5       115134464   117209087     1037312   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142446 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   204796619   102398278+   7  HPFS/NTFS/exFAT
/dev/sdb2       204796620   625137344   210170362+   f  W95 Ext'd (LBA)
/dev/sdb5       204796683   409593239   102398278+   7  HPFS/NTFS/exFAT
/dev/sdb6       409593303   625137344   107772021    7  HPFS/NTFS/exFAT
david@david-Latitude-D620:~$ 

```

Here ya go...

---

### Post by J_Me on 2013-12-18
The swap space is on the fastest part of your disk, so that's ok. You could try updating/cleaning ubuntu with ```
 sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean 
```

---

### Post by Impavidus on 2013-12-18
With firefox eating 20% of your ram, other programs must still eat the remaining 80%. I see you only have 1GB ram in your machine. Which desktop environment do you run? Switching to Xubuntu may help.

---

### Post by dwjeanes2 on 2013-12-18
> **Impavidus said:**
> With firefox eating 20% of your ram, other programs must still eat the remaining 80%. I see you only have 1GB ram in your machine. Which desktop environment do you run? Switching to Xubuntu may help.


Yes, it is clear that 1 gig isn't sufficient, however, this is an old laptop, and upgrading it isn't a wise investment. I just want to determine what I CAN run, under the constraints of the system, rather than identify shortcomings in a nearly decade old machine. I use the default desktop, at least I don't think I ever chose anything else. Since I use a minimal app set, and do no development on this machine, the environment is of minimal relevance. I just use the apps mentioned above, with a very rare usage of the office suite, and I will happily swap out the browser in favor of a spreadsheet when need dictates. 

I hope that my answer isn't abrupt, no intent to offend or show offense, I just want the situation known, so that inappropriate suggestions are minimized, i.e. I'm not going to buy more memory for this machine.

 To summarize to this point, it seems that the memory is the likely culprit. Is Xubuntu better at managing resources when they are scarce?

One last note: I have not changed usage habits, the only real changes in my system are system and app upgrades, which I allow Ubuntu to do unimpeded. The one thing that I know changed just before this issue arose was the latest ubuntu upgrade, fwiw.

Finally, thanks to all who have and will respond to my issue. This is a  great community, and I always find good advice here. Ubuntu and it's  userbase/community rocks!

---

### Post by philinux on 2013-12-18
Xubuntu is just lighter on resources thats all.

---

### Post by mörgæs on 2013-12-18
> **dwjeanes2 said:**
> this is an old laptop, and upgrading it isn't a wise investment.

A fresh install of Lubuntu 13.10 would indeed be wise.

---

### Post by Impavidus on 2013-12-18
That was my suggestion too. Xubuntu uses less ram for itself, leaving more for your applications without resorting to swap. I use it comfortably on a 1GB memory machine. Lubuntu is even lighter. You can convert to Xubuntu by installing the xubuntu-desktop package and then switch to the Xubuntu desktop in the login screen. The default interface will still sit on your hard drive, but won't be loaded, so it doesn't use any memory.

If you like it, you can do a full conversion. This means cleaning up a lot of Ubuntu stuff, so it may be easier (and cleaner, which will prevent future surprises) to do a clean install of Xubuntu.

The same applies for Lubuntu, except that 12.04 is no longer supported. You'd have to do a clean install of 13.10 anyway.

---

### Post by dwjeanes2 on 2013-12-18
> **mörgæs said:**
> A fresh install of Lubuntu 13.10 would indeed be wise.

That may well be my next step. I will also consider Xubuntu, since it offers an upgrade path.  I thank you all for the help and advice.

---

