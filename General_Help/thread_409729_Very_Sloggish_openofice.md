---
title: "Very Sloggish openofice"
date: 2007-04-14
forum: General Help
---

### Post by thoeng on 2007-04-14
Hi All,

I am having problem of doing my work on openoffice.xls. It seems become very very sluggish for 10 secs every 30 secs  ... is there any way i can found out the problem ?
is that possible that I have installed beryl so the perfomance is not sufficient anymore ?

my detail:

processor: AMD athlon XP 1800+
Ram: 512MB
Graphic: Nvidia 5700VE 128mb
HD: 160GB 7200


PLease help as i needed it desperately to do my work ,. otherwise i don't see any reason why should i migrate from windows. I love feisty fawn and its beryl effect but this start to stress me down


Erin.

---

### Post by PilotJLR on 2007-04-14
For starters, run "top" in a terminal and see exactly what process is slowing the machine down...

Also try using openoffice without Beryl to see if that is the issue.

---

### Post by PilotJLR on 2007-04-14
And more importantly - have you installed the nvidia driver?? Cause if not then that could easily be the issue.

---

### Post by thoeng on 2007-04-14
Hi and thanks for replying desperate man thread, this is i am seeing when i run top on terminal


top - 11:37:30 up  1:27,  2 users,  load average: 1.04, 1.08, 0.78
Tasks:  97 total,   2 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.7%us,  4.3%sy,  0.0%ni, 65.9%id,  0.0%wa,  1.7%hi, 13.4%si,  0.0%st
Mem:    515988k total,   505268k used,    10720k free,    19760k buffers
Swap:   498004k total,   118068k used,   379936k free,   183044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 4750 root      15   0  144m  59m 7200 S 11.3 11.8   8:47.69 Xorg                                                                                            
 5323 eri       15   0  114m  33m 4600 R  5.0  6.6   1:48.64 beryl                                                                                           
 5828 root      15   0 71724  31m  19m S  1.3  6.2   0:23.33 synaptic                                                                                        
 5002 slimserv  15   0 53748  22m 2256 S  0.7  4.6   0:39.29 slimserver                                                                                      
 5857 eri       15   0 78012  17m  11m S  0.7  3.4   0:01.80 gnome-terminal                                                                                  
 5130 slimserv  15   0 96444 5388 2928 S  0.3  1.0   0:02.18 mysqld                                                                                          
 5769 eri       15   0  205m  71m  27m S  0.3 14.2   1:46.68 firefox-bin                                                                                     
 5832 root      15   0  4972 1924 1652 S  0.3  0.4   0:04.06 http                                                                                            
 5877 eri       15   0  2316 1156  880 R  0.3  0.2   0:00.14 top                                                                                             
    1 root      18   0  2912 1808  488 S  0.0  0.4   0:01.28 init                                                                                            
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0                                                                                     
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 events/0                                                                                        
    6 root      17  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                                                         
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                                                         
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                                                       
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
   95 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                         
  118 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush                                                                                         
  119 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush                                                                                         
  120 root      10  -5     0    0    0 S  0.0  0.0   0:00.39 kswapd0                                                                                         
  121 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1930 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1931 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 2142 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                                           
 2143 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 2309 root      10  -5     0    0    0 S  0.0  0.0   0:00.12 kjournald                                                                                       
 2508 root      21  -4  2864  452  376 S  0.0  0.1   0:00.67 udevd                                                                                           
 3398 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                       
 3594 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                                                      
 3863 root      18   0  3772 1036  620 S  0.0  0.2   0:04.37 mount.ntfs-3g                                                                                   
 4161 root      18   0  1652  508  440 S  0.0  0.1   0:00.00 getty                                                                                           
 4162 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty                                                                                           
 4164 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty                                                                                           
 4168 root      18   0  1648  504  440 S  0.0  0.1   0:00.00 getty                                                                                           
 4169 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty                                                                                           
 4170 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty                                                                                           
 4414 root      18   0  2256 1156  648 S  0.0  0.2   0:00.00 acpid                                                                                           
 4516 root      17   0  1700  640  536 S  0.0  0.1   0:00.04 syslogd                                                                                         
 4565 root      18   0  1788  520  432 S  0.0  0.1   0:00.04 dd                                                                                              
 4567 klog      18   0  2432 1368  400 S  0.0  0.3   0:00.09 klogd                                                                                           
 4588 messageb  15   0  2852 1000  728 S  0.0  0.2   0:00.16 dbus-daemon                                                                                     
 4604 haldaemo  15   0 10380 8560 1592 S  0.0  1.7   0:03.34 hald                                                                                            
 4605 root      15   0  2876 1044  888 S  0.0  0.2   0:00.04 hald-runner                                                                                     
 4611 haldaemo  18   0  2092  876  760 S  0.0  0.2   0:00.00 hald-addon-acpi

---

