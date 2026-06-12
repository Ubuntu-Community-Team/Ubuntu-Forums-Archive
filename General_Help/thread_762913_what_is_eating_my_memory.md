---
title: "what is eating my memory"
date: 2008-04-22
forum: General Help
---

### Post by oddworld on 2008-04-22
I cant find out whats using up all of my memory, I have 2 gigs RAM and 2 gigs SWAP, and both are nearly full! 
The numbers just don't add up.
Here is top:

```

top - 13:48:32 up 1 day, 23:17,  2 users,  load average: 1.17, 1.18, 1.09
Tasks: 141 total,   1 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.0%us,  9.6%sy,  0.6%ni, 81.7%id,  0.9%wa,  0.1%hi,  1.1%si,  0.0%st
Mem:   2075940k total,  1687536k used,   388404k free,     8704k buffers
Swap:  1759044k total,  1397176k used,   361868k free,   118924k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                             
    7 root      34  19     0    0    0 S   10  0.0 295:55.04 ksoftirqd/1                         
    4 root      34  19     0    0    0 S    6  0.0 157:20.41 ksoftirqd/0                         
22612 davis     15   0 1253m 133m 7236 S    4  6.6  11:51.18 VirtualBox                          
 5650 root      15   0  241m  56m  10m S    2  2.8 103:03.76 Xorg                                
 6136 davis     15   0  129m  10m 3592 S    2  0.5  39:39.13 compiz.real                         
24193 davis     15   0  2364 1088  792 R    2  0.1   0:00.01 top                                 
    1 root      18   0  2952  348  300 S    0  0.0   0:01.32 init                                
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                            
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                         
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                          
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                         
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                          
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                            
   10 root      10  -5     0    0    0 S    0  0.0   0:00.06 events/1                            
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                             
   31 root      10  -5     0    0    0 S    0  0.0   0:00.01 kblockd/0                           
   32 root      10  -5     0    0    0 S    0  0.0   0:00.12 kblockd/1                           
   33 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpid                              
   34 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                        
  130 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                             
  157 root      15   0     0    0    0 S    0  0.0   0:05.54 pdflush                             
  159 root      10  -5     0    0    0 S    0  0.0   0:43.93 kswapd0                             
  210 root      16  -5     0    0    0 S    0  0.0   0:00.00 aio/0                               
  211 root      16  -5     0    0    0 S    0  0.0   0:00.00 aio/1                               
 2054 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                               
 2055 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/1                               
 2056 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                             
 2059 root      13  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_0                           
 2068 root      10  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_1                           
 2136 root      13  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                            
 2156 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                       
 2159 root      16  -5     0    0    0 S    0  0.0   0:00.00 khubd                               
 2427 root      10  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                         
 2642 root      10  -5     0    0    0 S    0  0.0   0:07.68 kjournald                           
 2845 root      11  -4  3040  276  276 S    0  0.0   0:00.17 udevd                               
 4062 root      10  -5     0    0    0 S    0  0.0   0:00.23 rt61pci                             
 4381 root      15   0  4840 1880  520 S    0  0.1   4:33.14 mount.ntfs                          
 4384 root      15   0  3788  520  452 S    0  0.0   0:00.05 mount.ntfs                          
 4387 root      15   0  4440 1060  512 S    0  0.1   7:22.53 mount.ntfs                          
 4625 root      18   0  1696  256  256 S    0  0.0   0:00.00 getty                               
 4626 root      18   0  1692  256  256 S    0  0.0   0:00.00 getty                               
 4629 root      18   0  1696  256  256 S    0  0.0   0:00.00 getty                               
 4631 root      18   0  1692  256  256 S    0  0.0   0:00.00 getty                               
 4632 root      18   0  1696  256  256 S    0  0.0   0:00.00 getty                               
 4633 root      18   0  1692  256  256 S    0  0.0   0:00.00 getty                               
 4826 root      15   0  2432  424  424 S    0  0.0   0:00.00 acpid                               
 4875 root      10  -5     0    0    0 S    0  0.0   0:00.04 kondemand/0                         
 4876 root      20  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1                         
 4939 syslog    15   0  1916  452  376 S    0  0.0   0:35.33 syslogd                             
 4994 root      16   0  1836  252  236 S    0  0.0   0:58.49 dd                                  
 4996 klog      18   0  2488  348  304 S    0  0.0   0:39.33 klogd                               
 5017 messageb  18   0  3036  988  612 S    0  0.0   0:07.70 dbus-daemon                         
 5033 root      24   0 28956 1536 1340 S    0  0.1   0:01.01 NetworkManager                      
 5047 root      15   0  3276  888  800 S    0  0.0   0:00.00 NetworkManagerD                     
 5060 root      25   0  3088  492  492 S    0  0.0   0:00.00 system-tools-ba                     
 5062 root      25   0  2772  708  708 S    0  0.0   0:00.00 dbus-daemon                         
 5080 haldaemo  17   0  5660 1612 1052 S    0  0.1   0:04.98 hald                                
 5081 root      16   0  3096  572  572 S    0  0.0   0:00.00 hald-runner                         
 5137 haldaemo  24   0  2164  484  484 S    0  0.0   0:00.00 hald-addon-keyb                     
 5144 haldaemo  15   0  2160  484  484 S    0  0.0   0:00.02 hald-addon-keyb                     
davis@davis-desktop:~$ 

```

---

### Post by Het Irv on 2008-04-22
I saw Vbox on that list, do you have a Virtual Machine running?
If so that will eat into your RAM.  But I do see what you mean about the numbers not adding up.

---

### Post by oddworld on 2008-04-22
I gave virtualbox 1 gig of RAM, and earlier it was reporting using that 1 gig. Virtualbox is still running but now it is not reporting using that 1 gig.
Any ideas?

---

### Post by Sirhanz on 2008-04-22
I think it is that maybe virtual box crashed and that 1 gig of ram is being reserved. Try disabling virtual box from starting up, reboot and then check the readings.

---

### Post by Het Irv on 2008-04-22
If I have got this right, VB is going to allocate 1 gig for the Virtual Machine and not let the base computer touch those resources.  But that still doesn't add up.

You could try rebooting your computer to clear your RAM and Swap.  If you haven't rebooted in a while it could just be bits and pieces that have been accumulating like dust.

---

### Post by oddworld on 2008-04-22
Yea I am sure that rebooting will fix the problem, I just didn't know why it is not adding up.
Earlier when I allowed virtualbox 1 gig of ram, my total ram used went from 300megs to 1.3 gigs - just as it should.
Now the ram has slowly increased to 1.8 gigs (which could be normal), but there is 1.4 gigs of swap that came out of nowhere. Swap was empty before.

I don't mind using so much RAM if the computer told me why I was using it.
if top does not report it, is there another way of telling why / if there is a memory leak?
P.S. the computer has an uptime of 2 days (not long at all)

---

### Post by Het Irv on 2008-04-22
Were you using any other high memory apps during the two days?
But I agree you have a memory leak somewhere and I don't know how to find/plug it.

Firefox 2 watching youTube or something like that might have done it.

---

### Post by bingoUV on 2008-04-22
1. Try sorting top output by memory usage (shift - m)
2. Memory used could be buffers. At a particular moment memory required might have shot up , some applications requested a lot of memory and released it. This could have swap space to be used. If applications are not swapping now, swap may not get empty. To figure it out, post the output of 
```

cat /proc/meminfo

```

---

### Post by oddworld on 2008-04-22
top by memory:

```
top - 15:23:29 up 2 days, 52 min,  2 users,  load average: 1.20, 1.49, 1.40
Tasks: 142 total,   2 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us, 10.0%sy,  0.0%ni, 87.2%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:   2075940k total,  1718044k used,   357896k free,    46024k buffers
Swap:  1759044k total,  1442032k used,   317012k free,   152340k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                     
24863 davis     15   0  205m  88m  22m S    0  4.4   1:14.56 firefox-bin                 
 5650 root      15   0  248m  62m 9108 S    1  3.1 106:56.19 Xorg                        
22612 davis     15   0 1253m  57m 6732 R    3  2.9  15:25.27 VirtualBox                  
 8262 davis     16   1  191m  28m 7076 S    0  1.4  37:43.93 linuxdcpp                   
 6574 davis     15   0  122m  21m 7624 S    0  1.1   3:01.56 pidgin                      
23766 davis     15   0 97844  19m  10m S    0  0.9   0:04.17 nautilus                    
 6219 davis     18   0 83832  18m 5704 S    0  0.9   0:06.09 deskbar-applet              
 6014 davis     18   0 61076  14m 6812 S    0  0.7   1:07.30 gnome-panel                 
 6921 davis     15   0  150m  11m 4792 S    0  0.5   9:59.48 amarokapp                   
 6136 davis     15   0  139m 8640 3612 S    0  0.4  40:49.08 compiz.real                 
 6135 davis     17   0 43112 7760 4176 S    0  0.4   0:30.48 gtk-window-deco             
 6168 davis     15   0 28180 5684 4380 S    0  0.3   0:02.00 python                      
 6221 davis     15   0 20628 5184 4144 S    0  0.2   0:34.93 multiload-apple             
 8671 davis     15   0 87540 5144 3684 S    0  0.2   0:01.48 VirtualBox                  
 6164 davis     15   0 63124 5084 4056 S    0  0.2   0:01.69 nm-applet                   
 6147 davis     15   0 47420 4952 4136 S    0  0.2   0:02.23 update-notifier             
 6900 davis     17   0 42504 4620 3500 S    0  0.2   0:03.16 notification-da             
 6255 davis     15   0 45308 4492 3752 S    0  0.2   0:00.49 fast-user-switc             
 6175 davis     15   0 45528 4372 3472 S    0  0.2   0:04.78 gnome-power-man             
 6217 davis     15   0 54836 4172 3856 S    0  0.2   0:00.48 mixer_applet2               
 6187 davis     15   0 77724 4112 3840 S    0  0.2   0:00.66 trashapplet                 
 6150 davis     18   0 69204 3940 3424 S    0  0.2   0:00.23 evolution-alarm             
 8680 davis     15   0 63404 3788 2364 S    0  0.2   0:09.78 VBoxSVC                     
 6008 davis     15   0 38932 3672 3124 S    0  0.2   0:06.25 gnome-settings-             
 5963 davis     22   0 27976 3196 2804 S    0  0.2   0:00.34 x-session-manag             
25033 davis     15   0  5720 3080 1424 S    0  0.1   0:00.22 bash                        
 6206 davis     15   0 36696 3016 2784 S    0  0.1   0:00.06 evolution-excha             
 6934 davis     15   0 28484 2960 2552 S    0  0.1   0:02.93 kded                        
 6143 davis     18   0 13576 2660 2428 S    0  0.1   0:00.19 bluetooth-apple             
 6154 davis     34  19 27984 2508 1524 S    0  0.1   0:03.57 trackerd                    
 6002 davis     18   0  6724 2484 1256 S    0  0.1   0:01.40 gconfd-2                    
 6141 davis     15   0 19500 2428 2424 S    0  0.1   0:00.06 vino-session                
 6023 davis     18   0 20388 2424 2100 S    0  0.1   0:02.40 gnome-volume-ma             
25028 root      16   0  8044 2408 1956 S    0  0.1   0:00.03 sshd                        
 6157 davis     15   0 11552 2136  984 S    0  0.1   0:07.08 xscreensaver                
 6225 davis     15   0 58784 2052 1628 S    0  0.1   0:00.07 evolution-data-             
 4381 root      15   0  4972 1984  488 S    0  0.1   4:38.68 mount.ntfs                  
 6932 davis     15   0 25648 1964 1756 S    0  0.1   0:00.04 klauncher                   
 6028 davis     15   0 40888 1952 1392 S    0  0.1   0:00.25 bonobo-activati             
 6085 davis     15   0  8748 1880 1620 S    0  0.1   0:01.05 gnome-vfs-daemo             
 6137 davis     15   0 16728 1800 1436 S    0  0.1   1:11.00 gnome-screensav             
 5184 root      15   0 10836 1736  396 S    0  0.1   0:02.68 hald-addon-hid-             
23778 davis     15   0 10292 1692 1192 S    1  0.1   0:58.67 conky                       
 5080 haldaemo  18   0  5660 1620 1056 S    0  0.1   0:05.15 hald                        
 6924 davis     16   0 25788 1584 1536 S    0  0.1   0:00.09 kdeinit                     
25032 davis     15   0  8044 1552 1080 S    0  0.1   0:00.00 sshd                        
 5033 root      15   0 28956 1544 1348 S    0  0.1   0:01.05 NetworkManager              
 6929 davis     15   0 25500 1456 1404 S    0  0.1   0:00.05 dcopserver                  
 6946 davis     15   0 26528 1440 1392 S    0  0.1   0:00.00 kio_file                    
davis@davis-desktop:~$ 

```


and cat /proc/meminfo

```
davis@davis-desktop:~$ cat /proc/meminfo
MemTotal:      2075940 kB
MemFree:        358044 kB
Buffers:         46144 kB
Cached:         152372 kB
SwapCached:    1204208 kB
Active:         400284 kB
Inactive:      1250596 kB
HighTotal:     1179584 kB
HighFree:       102264 kB
LowTotal:       896356 kB
LowFree:        255780 kB
SwapTotal:     1759044 kB
SwapFree:       317012 kB
Dirty:             124 kB
Writeback:           0 kB
AnonPages:      284260 kB
Mapped:          52360 kB
Slab:            36256 kB
SReclaimable:     8356 kB
SUnreclaim:      27900 kB
PageTables:       4548 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2797012 kB
Committed_AS:  2515232 kB
VmallocTotal:   114680 kB
VmallocUsed:     47676 kB
VmallocChunk:    61428 kB
davis@davis-desktop:~$ 

```

---

### Post by yaknowwat on 2008-04-22
There might possibly be something in your root that is having a memory leak

mind doing a sudo top

---

### Post by bingoUV on 2008-04-22
Yes, no need to worry. Most of swap is swapcache i.e. 
Swap(1442032k) - SwapCache (1204208k) is negligible. So much might have been modified after stuff was swapped in again. So don't count swap. You are not getting the sluggishness that active swapping produces.

From your top, we can account for 2075940 - (358044+46144+152372)kb = 1519380kb of memory usage easily.

---

### Post by oddworld on 2008-04-22
```
davis@davis-desktop:~$ sudo top
[sudo] password for davis:

top - 16:10:11 up 2 days,  1:39,  2 users,  load average: 0.68, 0.91, 1.02
Tasks: 141 total,   1 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us, 10.1%sy,  0.2%ni, 86.7%id,  0.0%wa,  0.0%hi,  1.7%si,  0.0%st
Mem:   2075940k total,  1118896k used,   957044k free,    50112k buffers
Swap:  1759044k total,   867336k used,   891708k free,   157956k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
24863 davis     15   0  206m  89m  22m S    1  4.4   1:39.53 firefox-bin        
 5650 root      15   0  236m  59m 6252 S    1  3.0 107:31.37 Xorg               
 8262 davis     16   1  191m  28m 7076 S    0  1.4  37:53.24 linuxdcpp          
 6574 davis     15   0  123m  22m 7624 S    0  1.1   3:03.67 pidgin             
23766 davis     15   0 97844  19m  10m S    0  0.9   0:04.17 nautilus           
 6219 davis     15   0 83832  18m 5704 S    0  0.9   0:06.09 deskbar-applet     
 6014 davis     18   0 61076  14m 6812 S    0  0.7   1:07.33 gnome-panel        
 6921 davis     15   0  150m  11m 4792 S    0  0.5  10:05.23 amarokapp          
 6136 davis     15   0  135m 8712 3604 S    1  0.4  41:14.98 compiz.real        
 6135 davis     19   0 43112 7764 4176 S    0  0.4   0:30.49 gtk-window-deco    
 8671 davis     15   0 87540 6272 4668 S    0  0.3   0:01.53 VirtualBox         
 6168 davis     15   0 28180 5684 4380 S    0  0.3   0:02.02 python             
 8680 davis     15   0 63404 5276 2868 S    0  0.3   0:09.94 VBoxSVC            
 6221 davis     15   0 20628 5184 4144 S    0  0.2   0:35.31 multiload-apple    
 6164 davis     15   0 63124 5084 4056 S    0  0.2   0:01.69 nm-applet          
 6147 davis     18   0 47420 5076 4196 S    0  0.2   0:02.26 update-notifier    
 6900 davis     19   0 42504 4632 3500 S    0  0.2   0:03.17 notification-da    
davis@davis-desktop:~$ 

```

---

### Post by yaknowwat on 2008-04-22
I don't know what to say other than a leak in Virtual Box sorry

---

### Post by ninjagin on 2008-04-22
actually.. my system gets quite laggy at times too especially after i run firefox...

when i check at the memory ussage, i found that the firefox-bin occupies a huge chunk of memory.. is this normal?

---

### Post by Hickory420 on 2008-04-22
> **ninjagin said:**
> actually.. my system gets quite laggy at times too especially after i run firefox...

when i check at the memory ussage, i found that the firefox-bin occupies a huge chunk of memory.. is this normal?
Yes, Firefox is a memory hog... unfortunately. But that is not affecting oddworld. Firefox does not consistently take up 2 gigs of ram.

---

### Post by yaknowwat on 2008-04-22
Yeah firefox 2 is a memory hog but firefox 3 is not (due to all it's improvements) and Fx 3 beta 5 will be included in Hardy Heron which will be final on thursday

lots of stability and performance improves come with this release currently using the release canindate and its works magnificently.

---

