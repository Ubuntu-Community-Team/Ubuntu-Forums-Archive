---
title: "50% CPU usage - but nothing in Sytem Monitor!"
date: 2007-03-15
forum: General Help
---

### Post by Monker1980 on 2007-03-15
Hi,

I am a relatively new Ubuntu user - recently upgraded to Edgy from Dapper with hardly any issues. My CPU is a dual core AMD64 and recently I have noticed that each core is constantly on 50% usage in the System Monitor 'Resources' tab, but no processes are using anything like that under the 'Processes' tab. There are no hidden processes and I am displaying all processes.

Does anyone have any ideas what's going on?

Thanks,

James

---

### Post by dams on 2007-03-15
I don't think you have anything to worry about. The 50% CPU usage is only taking into account running processes and not idle time. If you start a console up and run top you should see that you have a high %id.

""CPU states" Shows the percentage of CPU time in user mode, system mode, niced tasks, iowait and idle. (Niced tasks are only those whose nice value is positive.) Time spent in niced tasks will also be counted in system and user time, so the total will be more than 100%." 
[http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)

---

### Post by mcduck on 2007-03-15
Try running 'top' in a terminal to check what's using the CPU. (to quit top press 'q')

---

### Post by Monker1980 on 2007-03-15
This is what 'top' says...

top - 11:21:36 up 1 day,  2:45,  3 users,  load average: 1.66, 1.67, 1.64
Tasks: 139 total,   1 running, 137 sleeping,   0 stopped,   1 zombie
Cpu(s): 23.6%us, 27.2%sy,  0.0%ni, 49.0%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   4045016k total,  1978280k used,  2066736k free,   455548k buffers
Swap:  6144820k total,        0k used,  6144820k free,   627828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
10475 james     18   0 10460 1020  760 S    5  0.0  56:57.91 acroread                                                                                        
 4671 root      15   0  154m  89m  15m S    2  2.3   5:38.04 Xorg                                                                                            
 4670 root      15   0 62708 2952 2160 S    1  0.1   5:19.20 gdm                                                                                             
28567 james     15   0  143m  21m  10m S    1  0.5   0:04.37 gnome-terminal                                                                                  
    5 root      RT   0     0    0    0 S    0  0.0   1:32.21 migration/1                                                                                     
13680 james     15   0  127m  19m  12m S    0  0.5   3:19.47 gnome-system-mo                                                                                 
28737 james     16   0 10764 1356  960 R    0  0.0   0:05.27 top                                                                                             
    1 root      16   0  2728  600  476 S    0  0.0   0:01.92 init                                                                                            
    2 root      RT   0     0    0    0 S    0  0.0   0:00.32 migration/0                                                                                     
    3 root      34  19     0    0    0 S    0  0.0   0:00.13 ksoftirqd/0                                                                                     
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      34  19     0    0    0 S    0  0.0   0:01.15 ksoftirqd/1                                                                                     
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    8 root      10  -5     0    0    0 S    0  0.0   0:00.12 events/0                                                                                        
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   11 root      10  -5     0    0    0 S    0  0.0   0:00.01 kthread                                                                                         
   15 root      10  -5     0    0    0 S    0  0.0   0:00.06 kblockd/0                                                                                       
   16 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                       
   17 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   18 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  154 root      10  -5     0    0    0 S    0  0.0   0:00.02 kseriod                                                                                         
  192 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  193 root      15   0     0    0    0 S    0  0.0   0:00.04 pdflush                                                                                         
  194 root      17   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                         
  195 root      12  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  196 root      12  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 1784 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                           
 1785 root      14  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                           
 1790 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
 1791 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                       
 1794 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                       
 1795 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                       
 1903 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                       
 1904 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                                                       
 1905 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                                                       
 1906 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_7                                                                                       
 1938 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 1968 root      10  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                        
 2001 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_8                                                                                       
 2002 root      10  -5     0    0    0 S    0  0.0   0:00.00 usb-storage                                                                                     
 2017 root      15   0     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                     
 2163 root      10  -5     0    0    0 S    0  0.0   0:05.06 kjournald                                                                                       
 2257 root      15   0  2696  584  488 S    0  0.0   0:00.00 logd                                                                                            
 2376 root      13  -4 11344 1516  376 S    0  0.0   0:00.18 udevd                                                                                           
 3183 root      12  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                       
 3206 root      11  -5     0    0    0 S    0  0.0   0:00.00 kgameportd

It looks like I have ~50% idle - the same thing that System Monitor tells me. The process using the most CPU is 'acroread' but that's only using 5% of the CPU.

---

### Post by mcduck on 2007-03-15
Well, it's not idle that's the problem. That's just telling the free time of your CPU.. :D

Anyway, the TIME column reports pretty high time for acroread, so that's what I'd blame first.. Try to not use acroread and see if that helps. (Evince is much lighter anyway)

---

### Post by Monker1980 on 2007-03-15
Bingo - acroread was the culprit. Strange how the acroread process didn't show up as using lots of CPU with top though...

Thanks for your help :)

---

### Post by mcduck on 2007-03-15
> **Monker1980 said:**
> Bingo - acroread was the culprit. Strange how the acroread process didn't show up as using lots of CPU with top though...

Thanks for your help :)

No problem. I recommend using Evince, the default viewer for PDF files, instead. It's way quicker and lighter than acroread anyway..

---

