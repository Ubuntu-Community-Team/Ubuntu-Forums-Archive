---
title: "Plz Help, Worked great now it doesn't"
date: 2008-02-07
forum: General Help
---

### Post by Anacranom on 2008-02-07
I have 7.10, all updates, and plenty of free space on all drives, tons of swap,,, My downloaded .avi, mpeg and other video files played perfect, example: RvD2 (Ryan vs. Dorkman 2) from stage 6, ok, now the player locks up- grays out, started first of this week. then my firefox starts locking up as well???, now firefox doesn't lock up but it takes FOREVER to reload, switch from Inbox to junk emails-or any other folder, or go to a link i click on a website??? That was a problem I could deal with,,, but now! (Possibly related) I have LAG,,, playing COH!!! I never had ANY lag in COH, EVER! That was one of the key points i made to windows users about playing coh with ZERO lag, so ok,,, add it all up and I'm thinking theres something thats not right with the system and may be related, can anyone help?

---

### Post by raffytaffy on 2008-02-07
Tun the command *top* in your terminal while you do some everyday tasks and see if anything is eating up too much cpu. This would be my first step into identifying this problem; also could try running system monitor.

---

### Post by Anacranom on 2008-02-07
did the sys monitor,,, am now doing the "top",,, will post back...OH and thanx for the reply!

---

### Post by Anacranom on 2008-02-08
and of course as soon as you pull in to the mechanic's shop, the car stops "squeaking"!

wbcadmin@wbcadmin-desktop:~$ top

top - 23:01:42 up  1:17,  2 users,  load average: 0.00, 0.05, 0.07
Tasks: 153 total,   3 running, 150 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.6%us,  2.7%sy,  0.0%ni, 80.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2061368k total,  1162496k used,   898872k free,    25096k buffers
Swap:  5188984k total,        0k used,  5188984k free,   671136k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                      
 6682 wbcadmin  15   0  665m 115m  25m S   19  5.7   1:26.38 firefox-bin                                                                  
 5974 root      15   0  134m  45m 9.9m R   17  2.2   1:17.72 Xorg                                                                         
 6339 wbcadmin  15   0  144m 3228 1880 S    1  0.2   0:01.77 gnome-screensav                                                              
 6460 wbcadmin  15   0  237m  29m  13m S    1  1.5   0:11.84 compiz.real                                                                  
 3891 root      10  -5     0    0    0 S    0  0.0   0:34.34 Ieee80211/0                                                                  
 6318 wbcadmin  15   0  285m  21m  13m S    0  1.1   0:02.03 gnome-panel                                                                  
 6777 wbcadmin  15   0  266m  27m  13m R    0  1.4   0:00.89 gnome-terminal                                                               
 6953 wbcadmin  15   0 19080 1360  972 R    0  0.1   0:01.41 top                                                                          
    1 root      18   0  5116 1968  572 S    0  0.1   0:01.48 init                                                                         
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                     
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                  
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                  
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                   
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                  
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                  
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                   
    9 root      10  -5     0    0    0 S    0  0.0   0:00.02 events/0                                                                     
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                     
   11 root      10  -5     0    0    0 S    0  0.0   0:00.01 khelper                                                                      
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                    
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                    
   32 root      12  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                       
   33 root      12  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                 
  133 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                      
  163 root      16   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                      
  164 root      15   0     0    0    0 S    0  0.0   0:00.01 pdflush                                                                      
  165 root      11  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                      
  218 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                        
  219 root      11  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                        
 2089 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                
 2090 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                        
 2118 root      10  -5     0    0    0 S    0  0.0   0:00.01 ata/0                                                                        
 2119 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                        
 2120 root      17  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                      
 2195 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                    
 2197 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                    
 2256 root      16  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                    
 2257 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                    
 2534 root      10  -5     0    0    0 S    0  0.0   0:00.05 kjournald                                                                    
 2732 root      16  -4 20192 2024  384 S    0  0.1   0:00.38 udevd                                                                        
 3886 root      20  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused

---

### Post by mbsullivan on 2008-02-08
Hi Anacranom,

Sorry it's not more helpful, but I don't see anything unusual with your "top" output.  You're not running out of memory, and the number and type of tasks running looks pretty typical.  

However, *nix installations don't typically suffer from bit rot, so there must be some issue causing your slowdown. Are you still experiencing slowdown? If so, check the output of:

```
free -m
```

as well as

```
cat /proc/meminfo
```

and 

```
/proc/swaps
```

in order to make sure that it's not a memory issue. You could also get a more convenient system monitor such as gkrellm or conky in order to actively check which programs are hogging the most memory and CPU cycles.

Sorry there's not more to say... Are you sure you haven't installed anything new or changed your installation lately?

Mike

---

### Post by Anacranom on 2008-02-08
I'll run those and reply back, the only thing i have done is updates, and i ran the uninstall/reinstall flash plugin, and that seemed to help a bit, still no videos though

---

### Post by Anacranom on 2008-02-08
well here's the results...

wbcadmin@wbcadmin-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013       1207        805          0         87        572
-/+ buffers/cache:        547       1465
Swap:         5067         12       5055
wbcadmin@wbcadmin-desktop:~$ cat /proc/meminfo
MemTotal:      2061368 kB
MemFree:        824928 kB
Buffers:         89776 kB
Cached:         586080 kB
SwapCached:      12304 kB
Active:         661884 kB
Inactive:       448600 kB
SwapTotal:     5188984 kB
SwapFree:      5176680 kB
Dirty:             352 kB
Writeback:           0 kB
AnonPages:      422444 kB
Mapped:          97512 kB
Slab:            67604 kB
SReclaimable:    45688 kB
SUnreclaim:      21916 kB
PageTables:      20972 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   6219668 kB
Committed_AS:  1138068 kB
VmallocTotal: 34359738367 kB
VmallocUsed:     46740 kB
VmallocChunk: 34359684091 kB
wbcadmin@wbcadmin-desktop:~$ /proc/swaps
bash: /proc/swaps: Permission denied
wbcadmin@wbcadmin-desktop:~$ sudo /proc/swaps
[sudo] password for wbcadmin:
sudo: /proc/swaps: command not found
wbcadmin@wbcadmin-desktop:~$

---

