---
title: "Ubuntu installation extremely slow on high-end laptop"
date: 2007-04-10
forum: General Help
---

### Post by fledder on 2007-04-10
hi all,


I'm encountering a hugely frustrating issue. I consider myself a newbie but found myself successfully installing Ubuntu Edgy and making everything work the way I want it on my new laptop. The laptop is powerful, it's an HP dual core 1,6 with 2GB of RAM, Nvidia Geforce 7200 and 2 100GB hard disks. At one point, I had it all working, including Beryl, and I even made a backup of that. 

Now, all of a sudden, my system performs about 10 times  slower than before. Everything continues to work, but even starting a simple command prompt takes as much as 1 minute before it opens. Firefox even longer. Once a program is loaded, the performance is acceptable, but still far worse than before.

All my hardware works and when I run "top" from the console, only a few percent of my CPU and memory are consumed. I believe that the severe decrease in performance occurred after a failed hibernate that led to a crash. Oddly enough, even when restoring to the backup made when the system was performing well, the problem is not fixed. This has me looking for the cause, but I'm clueless about it. I tried disabling Beryl, but the lag remains. 

I really would like to continue to run Ubuntu, but am desperate at getting my old performance back. This laptop is too expensive to be this slow :( . In fact, it has become pretty much unusable.

For the sake of reference, here is some output from "top":

top - 20:59:38 up 27 min,  2 users,  load average: 0.01, 0.14, 0.21
Tasks:  94 total,   2 running,  92 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.7%us,  2.3%sy,  0.0%ni, 82.0%id,  0.0%wa,  0.0%hi,  2.0%si,  0.0%st
Mem:   2074684k total,   694032k used,  1380652k free,   107480k buffers
Swap:  3984080k total,        0k used,  3984080k free,   359616k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5547 fchrista  15   0  103m  41m 7684 S  5.3  2.0   0:44.23 beryl              
 5994 fchrista  15   0  180m  52m  21m S  5.3  2.6   0:30.57 firefox-bin        
10252 fchrista  15   0 71432  15m  10m R  3.7  0.8   0:02.01 gnome-terminal     
 5145 root      15   0 99.5m  28m 8296 S  1.3  1.4   0:26.72 Xorg               
 3210 root      13  -2  1652  380  284 S  0.3  0.0   0:00.99 ipw3945d-2.6.17    
    1 root      16   0  1632  532  448 S  0.0  0.0   0:00.97 init               
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kacpid             
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 kacpi_notify       
  125 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 kseriod         

I would appreciate any help the community can give me on this one. Thanks in advance for anyone responding.

---

### Post by neoaddict on 2007-04-10
Did you install any packages before the slow-down occured?

Could you run the command:

```
free
```

and paste the results?

---

### Post by fledder on 2007-04-10
hi neoaddict,

hereby the output:

             total       used       free     shared    buffers     cached
Mem:       2074684     432044    1642640          0       9400     222312
-/+ buffers/cache:     200332    1874352
Swap:      3984080          0    3984080

the output has become irrelevant I think, because I solved the problem in the meanwhile. Applications that I launched were delayed for 30 seconds or more before they started. Now they start in less than a second. The solution: disabling ipv6, as explained in this thread:

[http://ubuntuforums.org/showthread.php?t=329463&highlight=slow+launch](http://ubuntuforums.org/showthread.php?t=329463&highlight=slow+launch)

> You disable ipv6 by editing

/etc/modprobe.d/aliases

and changing

alias net-pf-10 ipv6

to

alias net-pf-10 off

After a reboot that fixed my problem right away. I am still clueless what caused the problem in the first place, some event triggered it, but I do not know which. I never ever touched IPv6 settings before.

Still, thanks for your help. This community is great.

---

### Post by IcemanV9 on 2007-04-10
Better yet ...

In the terminal:

```
gksudo gedit /etc/modprobe.d/blacklist
```

Add this line:  [FONT="Courier New"]blacklist ipv6[/FONT]

Save the file and reboot your box.

After reboot, in the terminal:

```
ip a | grep inet6
```

If no output, then ipv6 is disabled.

---

### Post by neoaddict on 2007-04-10
@ fleeder: Must have been your funky network.  XD  IPv6 is enabled by default in Ubuntu.__

---

