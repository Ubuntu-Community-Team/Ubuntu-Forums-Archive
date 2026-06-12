---
title: "khubd using 100% cpu when external HD is plugged"
date: 2007-10-18
forum: General Help
---

### Post by sa_venkatesan on 2007-10-18
Hello Ubuntu experts, 

I have been using Feisty for the last 6 months and I'm loving it. However, during the last couple of days, the CPU usage has shot up to 100% and khubd is using about 90% of the CPU.  I tried restarting the system (power off/on) and even applied all the updates (including kernel) and still the CPU usage is 100%.  

I have 3-4 external hdds connected to this system via USB hub (most of them NTFS)  and this setup worked fine during the last 6 months but during the last couple of days CPU usage has shot up and I'm not sure what has changed. 

The following message is getting repeated over and over again in dmesg output. 

[ 2379.977207] hub 3-0:1.0: hub_port_status failed (err = -32)
[ 2379.981096] ehci_hcd 0000:00:13.2: port 6 resume error -110

If I boot the system without any of the external HDDs powered on,  it works okay but once I power on one of them, the CPU usage goes to 100% and stays there even if I unmount the hdd.

Here is the top and uname output. 

$ uname -a
Linux cowboy 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux


Tasks: 150 total,   5 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.7%us, 96.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2042600k total,   831968k used,  1210632k free,    72188k buffers
Swap:  1646620k total,        0k used,  1646620k free,   455880k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1958 root      20  -5     0    0    0 R 86.5  0.0  26:07.73 khubd              
 4715 root      15   0  1796  528  432 S  7.0  0.0   1:58.17 dd                 
 4662 root      15   0  1704  648  536 S  3.7  0.0   0:57.93 syslogd            
 6272 vsarana   15   0  284m 145m  25m R  1.0  7.3   1:30.48 firefox-bin        
 4717 klog      16   0  2544 1372  400 R  0.7  0.1   0:14.69 klogd              
 4912 root      15   0 64468  23m 7756 S  0.7  1.2   1:14.34 Xorg               
 5573 vsarana   15   0 56472 8240 6700 S  0.3  0.4   0:01.39 gnome-cups-icon    
 5715 vsarana   15   0 62428  16m  10m R  0.3  0.8   0:00.71 gnome-terminal     
 5782 vsarana   16   0  2320 1192  880 S  0.3  0.1   0:03.59 top                
    1 root      15   0  2908 1844  524 S  0.0  0.1   0:01.14 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kthread            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0     

Can anyone provide more insights? 

Thanks in advance,

with warm regards,
Venkat Saranathan.

---

### Post by sa_venkatesan on 2007-10-19
A brief update. Apparently the error was NOT caused by an external USB hub, I had the same  problem with nothing but the Mouse/KB connected to the system.  I had to disable USB 2.0 (sudo modprobe -r ehci_hcd) to get this thing working.

Here is a related link

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections)

Again, this is NOT a satisfactory solution but atleast things are stable.

with warm regards,
venkat

---

