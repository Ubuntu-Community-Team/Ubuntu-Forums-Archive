---
title: "Ubuntu 18.04 session lost after inactivity"
date: 2021-04-08
forum: General Help
---

### Post by riccardosl45 on 2021-04-08
Dear community,
I'm running Ubuntu 18.04 LTS on a laptop, it worked fine for the past years. Recently I tried vanilla gnome, that I uninstall it and continue to use Ubuntu desktop with a darktheme available in Tweaks. Recently my user session started to crash for no reason after some inactivity time. No restart.
I went for a walk, the PC was on, connected to power supplied, I came back the mouse was stuck after few seconds of clicking on the keyboard the ubuntu login screen was shown. All the open apps were gone, session lost, no crash report or alert.
How should I figure out the issue? Is there a specific file to look for logs?

I can provide details below. Thank you!
R

```

System:    Host: HP Kernel: 5.4.0-70-generic x86_64 bits: 64 gcc: 7.5.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4) dm: gdm3 Distro: Ubuntu 18.04.5 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP EliteBook 840 G1 v: A3009DC10303 serial: N/A
           Mobo: Hewlett-Packard model: 198F v: KBC Version 15.59 serial: N/A
           BIOS: Hewlett-Packard v: L71 Ver. 01.47 date: 04/18/2019
           Chassis: type: 10 serial: N/A
Battery    BAT0: charge: 43.9 Wh 96.3% condition: 45.6/45.6 Wh (100%) volts: 12.5/11.2
           model: Hewlett-Packard Primary serial: <filter>status: N/A
CPU:       Dual core Intel Core i5-4300U (-MT-MCP-) arch: Haswell rev.1 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9977
           clock speeds: min/max: 800/2900 MHz 1: 1191 MHz 2: 1289 MHz 3: 1394 MHz 4: 1297 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:0a16
           Display Server: wayland (X.Org 1.19.6 ) driver: i915 Resolution: 1600x900@59.95hz, 2560x1440@59.91hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 4400 (HSW GT2)
           version: 4.5 Mesa 20.0.8 (compat-v: 3.0) Direct Render: Yes
Audio:     Card-1 Intel 8 Series HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:9c20
           Card-2 Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0 chip-ID: 8086:0a0c
           Sound: Advanced Linux Sound Architecture v: k5.4.0-70-generic
Network:   Card-1: Intel Ethernet Connection I218-LM
           driver: e1000e v: 3.2.6-k port: 3080 bus-ID: 00:19.0 chip-ID: 8086:155a
           IF: enp0s25 state: down mac: <filter>
           Card-2: Intel Wireless 7260 driver: iwlwifi bus-ID: 02:00.0 chip-ID: 8086:08b1
           IF: wlo1 state: up mac: <filter>
Drives:    HDD Total Size: 756.2GB (7.2% used)
           ID-1: /dev/sdb model: TS256GMTS400 size: 256.1GB serial: <filter> temp: 26C
           ID-2: /dev/sda model: HGST_HTS725050A7 size: 500.1GB serial: <filter> temp: 0C
Partition: ID-1: / size: 42G used: 27G (70%) fs: ext4 dev: /dev/sdb5
           ID-2: /home size: 49G used: 25G (53%) fs: ext4 dev: /dev/sdb6
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 46.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 296 Uptime: 6:20 Memory: 2650.3/15910.4MB Init: systemd v: 237 runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201 running in gnome-terminal-) inxi: 2.3.56 


```

---

### Post by riccardosl45 on 2021-04-09
TOP
```

top - 21:22:48 up  6:22,  1 user,  load average: 1.54, 1.51, 1.70
Tasks: 293 total,   1 running, 229 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.6 us,  1.0 sy,  0.0 ni, 95.0 id,  0.0 wa,  0.0 hi,  0.4 si,  0.0 st
KiB Mem : 16292288 total,  7780112 free,  2366400 used,  6145776 buff/cache
KiB Swap:  2036456 total,  2036456 free,        0 used. 12723776 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+  COMMAND                                                                               
 9278 myself    20   0 3693004 536908 191684 S   5.3  3.3   1:54.23  firefox                                                                               
 8980 myself    20   0 4031524 291560 155844 S   5.0  1.8   0:53.44  gnome-shell                                                                           
10167 myself    20   0 2868740 223120 142108 S   2.6  1.4   0:34.04 Web  Content                                                                           
 9376 myself    20   0 3099336 246672 121348 S   1.3  1.5   0:09.87 Web  Content                                                                           
 8994 myself    20   0 1551588 217692 183108 S   1.0  1.3   0:24.57  Xwayland                                                                              
 9461 myself    20   0 3076092 295792 102000 S   1.0  1.8   0:30.34  WebExtensions                                                                         
12114 myself    20   0   45780   4120   3424 R   1.0  0.0   0:00.05 top                                                                                    
 1532 root      20   0  269956   6088   5088 D   0.7  0.0   3:28.89  iio-sensor-prox                                                                       
 9333 myself    20   0 2726892 166544 101464 S   0.7  1.0   0:12.90 Web  Content                                                                           
 9638 myself    20   0  561740  43228  32564 S   0.7  0.3   0:03.05  gnome-terminal-                                                                       
10221 myself    20   0 2839736 287004 157684 S   0.7  1.8   0:16.29 Web  Content                                                                           
    1 root      20   0  226392  10052   6744 S   0.3  0.1   0:09.06  systemd                                                                               
  214 root       0 -20       0      0      0 I   0.3  0.0   0:00.65  kworker/2:1H-ev                                                                       
 1599 gdm       20   0 3884724 216844 157748 S   0.3  1.3   0:39.75  gnome-shell                                                                           
 8812 root      20   0       0      0      0 I   0.3  0.0   0:00.87  kworker/u16:2-e                                                                       
10120 myself    20   0 2867580 237516 151660 S   0.3  1.5   0:26.65 Web  Content                                                                           
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00  kthreadd                                                                              
    3 root       0 -20       0      0      0 I   0.0  0.0   0:00.00  rcu_gp                                                                                
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00  rcu_par_gp                                                                            
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00  kworker/0:0H-kb                                                                       
    9 root       0 -20       0      0      0 I   0.0  0.0   0:00.00  mm_percpu_wq                                                                          
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.18  ksoftirqd/0                                                                           
   11 root      20   0       0      0      0 I   0.0  0.0   0:10.42  rcu_sched                                                                             
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.15  migration/0                                                                           
   13 root     -51   0       0      0      0 S   0.0  0.0   0:00.00  idle_inject/0                                                                         
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00  cpuhp/0                                                                               
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1         

```

---

