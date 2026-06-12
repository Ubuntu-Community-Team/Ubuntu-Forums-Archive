---
title: "Love the os, just having minor problems"
date: 2018-06-19
forum: General Help
---

### Post by mrpingaz on 2018-06-19
Got rid of windows, don't game anymore to be honest and just need a solid os for general tasks.

Used to use ubuntu years back and got it on my system straight away. Hardware specs before i state some problems-

i5 6500 3,20 ghz
nvidia gtx 1050ti
8gb ram
SSD,
HDD

Web browser scrolling is really laggy, some youtube videos lag a bit playing too, using nvidia driver 390 was having the same issue with xorg drivers.

Takes a bit of time for apps to load, but i think its related to the next problem which is high cpu usage. two cores always seem to be at 100% fans go mad etc 

is it just hardware compatability issues or some drivers missing?

---

### Post by TheFu on 2018-06-19
Can't tell much from the information provided. Did you look at log files for hardware issues?
"Browser" is a generic term.  Which browser?   Chromium? Firefox? Dillo? Lynx?
Which apps are slow to load?
Which apps are using the CPU, RAM, Swap?

[https://www.tecmint.com/command-line-tools-to-monitor-linux-performance/](https://www.tecmint.com/command-line-tools-to-monitor-linux-performance/) has some tools that will be helpful as you gather data.

Without facts, it is impossible to troubleshoot. Best to setup some system monitoring that runs every minute or two and creates nice graphs for about 40 different system performance issues.  I use munin.

---

### Post by Hewjr100 on 2018-06-19
I had the same issues with my Nvidia Gtx 1050.  For me it was better to blacklist nouveau.  Scrolling and video was better.  In order to do it I had to boot into recovery mode and then followed this tutorial to blacklist nouveau.

[https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-disable-nouveau-nvidia-driver-on-ubuntu-18-04-bionic-beaver-linux)

Henry

---

### Post by mrpingaz on 2018-06-19
using firefox, tried chrome and chomonium all run the same, sometimes the text appears to tear scrolling. in terms of apps pretty much everything from opening text editors to opening browsers etc. Ram is never heavily used hasn't went over 2gigs of used data. CPU usage is most at streaming youtube videos. I did some commands and ubuntu is properly rendering with the GPU etc and using the 1050ti as i've disabled onboard graphics via the motherboard anyway so it wouldn't pick up any integrated graphics. 

this is the top output from just running firefox, apps sometimes don't load at all. System manager wont boot at all along with some other apps. 

```
top - 23:48:41 up 1 day, 55 min,  2 users,  load average: 1.12, 0.53, 0.23
Tasks: 268 total,   1 running, 221 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.9 us,  4.6 sy,  0.0 ni, 90.9 id,  1.5 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem :  8119936 total,  1058312 free,  2016956 used,  5044668 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  5895684 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 5475 root      20   0  377692  87184  68300 S  14.0  1.1   3:42.92 Xorg        
 5579 neil      20   0 4017928 269028  91648 S   8.0  3.3   4:14.33 gnome-shell 
25857 neil      20   0  572588 143960  88524 S   3.7  1.8   0:03.83 steam       
25468 neil      20   0  803384  37160  28096 S   2.0  0.5   0:01.53 gnome-term+ 
 1123 root     -51   0       0      0      0 S   1.0  0.0   3:11.77 irq/125-nv+ 
  856 root      20   0    4552    728    664 S   0.3  0.0   0:21.50 acpid       
 1163 plex      20   0  630104  72512  37408 S   0.3  0.9   3:39.90 Plex Media+ 
 1374 plex      35  15 1736628  57432   9428 S   0.3  0.7   2:59.29 Plex Scrip+ 
25217 neil      20   0 1859200 283544 143964 S   0.3  3.5   0:25.84 Web Content 
25280 neil      20   0 1677988 163492  93564 S   0.3  2.0   0:04.15 Web Content 
25487 neil      20   0   51324   3912   3252 R   0.3  0.0   0:00.82 top         
    1 root      20   0  225756   9380   6560 S   0.0  0.1   0:08.74 systemd     
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:+ 
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_+ 
    7 root      20   0       0      0      0 S   0.0  0.0   2:02.72 ksoftirqd/0 
    8 root      20   0       0      0      0 I   0.0  0.0   0:12.89 rcu_sched
```

---

