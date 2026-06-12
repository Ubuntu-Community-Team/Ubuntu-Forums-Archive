---
title: "Swap usage 100%"
date: 2006-10-26
forum: General Help
---

### Post by jcrocholl on 2006-10-26
Hi,

I'm running Dapper on several machines. On one of them, the swap is getting used up completely after some days of uptime. This makes the system run very slow. I think this has also happened before the last reboot 11 days ago, but before that the system was running okay for several months.

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:           250        235         14          0         27        168
-/+ buffers/cache:         39        210
Swap:          747        747          0

```

The system has been running for 11 days now and performed very many Firefox and Opera starts, in tightvncserver. But the kernel should release memory after a process is killed, right?

I have manually killed a lot of processes, and the memory is still full. Below is the output from top, including all running processes. The largest virtual memory use per process is less than 8 MB for sshd. Shouldn't the numbers in the VIRT column add up to the total memory usage?

```

$ top -bn1
top - 04:56:52 up 11 days,  3:48,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  36 total,   1 running,  35 sleeping,   0 stopped,   0 zombie
Cpu(s): 19.9% us,  7.4% sy,  0.4% ni, 61.3% id,  7.6% wa,  1.1% hi,  2.3% si
Mem:    256292k total,   241480k used,    14812k free,    27868k buffers
Swap:   765944k total,   765944k used,        0k free,   172832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      16   0  1564  116   64 S  0.0  0.0   0:32.54 init               
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.34 events/0           
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    8 root      10  -5     0    0    0 S  0.0  0.0   1:07.87 kblockd/0          
   65 root      15   0     0    0    0 S  0.0  0.0   0:46.77 pdflush            
   66 root      15   0     0    0    0 S  0.0  0.0   0:55.81 pdflush            
   68 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
   67 root      15   0     0    0    0 S  0.0  0.0   6:52.25 kswapd0            
  657 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
 1723 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd              
 1805 root      15   0     0    0    0 S  0.0  0.0   4:33.98 kjournald          
 2780 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event      
 3209 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald          
 4057 root      15   0     0    0    0 S  0.0  0.0   0:00.68 kapmd              
 4188 root      17   0  4760  368  168 S  0.0  0.1   0:00.30 sshd               
 4297 root      18   0  1964   84    0 S  0.0  0.0   0:00.00 hcid               
 4312 root      20   0  1612   68    0 S  0.0  0.0   0:00.00 sdpd               
 4325 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd           
 4338 root      16   0  1624  160  100 S  0.0  0.1   0:04.91 mdadm              
 4380 daemon    17   0  1796  120   44 S  0.0  0.0   0:00.00 atd                
 4395 root      15   0  2120  300  148 S  0.0  0.1   0:19.07 cron               
 4468 root      16   0  1564   72    0 S  0.0  0.0   0:00.00 getty              
 4469 root      16   0  1564   72    0 S  0.0  0.0   0:00.00 getty              
 4470 root      16   0  1560   64    0 S  0.0  0.0   0:00.00 getty              
 4471 root      16   0  1564   72    0 S  0.0  0.0   0:00.00 getty              
 4472 root      16   0  1560   68    0 S  0.0  0.0   0:00.00 getty              
15255 root      17   0  1560   68    0 S  0.0  0.0   0:00.00 getty              
21148 dnsmasq   16   0  3072  836  612 S  0.0  0.3   0:00.10 dnsmasq            
21280 root      16   0  2712  860  660 S  0.0  0.3   0:00.09 pppd               
23235 root      15   0  7520 2372 1976 S  0.0  0.9   0:00.16 sshd               
23237 shotfact  15   0  7520 1504 1100 S  0.0  0.6   0:00.00 sshd               
23238 shotfact  15   0  5616 3328 1416 S  0.0  1.3   0:00.64 bash               
23255 shotfact  15   0  2192  952  756 R  0.0  0.4   0:00.00 top                

```

Where is all that memory being used?

How can I analyze this problem further?

Thanks for your time,
Johann

---

### Post by po0f on 2006-10-26
jcrocholl,

Do you leave programs running forever on that box?  Something could be leaking memory.

---

### Post by jcrocholl on 2006-10-26
If I understand correctly, a memory leak would only occur while the program is still running, because the memory gets freed by the kernel when a program dies.

My original post includes a list of all processes that are still running on the machine. It seems that none of them is using more than 8 megs of virtual memory.

---

