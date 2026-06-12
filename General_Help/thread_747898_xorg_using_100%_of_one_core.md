---
title: "xorg using 100% of one core"
date: 2008-04-07
forum: General Help
---

### Post by RoyalPro on 2008-04-07
Xorg is using 90+% of one core on my 4200+.  I am using the Nvidia drivers Linux-x86_64-169.12 on my 8.04 (beta) Ubuntu 64 bit for my 6200 vid card.  I notice the high cpu usage when I have MythTV running, but MythTV only uses 5-7% of the CPU like it did before I did a fresh "upgrade" to 8.04.  My CPU speed used to slow down to 1GHz from 2.2 when using MythTV on my 7.10 Ubuntu 32 bit setup, but now it stays at 2.2 while MythTV is running and then slows down to 1GHz when I exit it.
Is this a Xorg problem, a MythTV problem, a Nvida driver problem, all of the above, none of the above, or something else?
Any help would be great and appreciated becasue I don't want my MythTV box running at 100$ all the time.
If you need more info let me know.

---

### Post by Crafty Kisses on 2008-04-07
Weird, let's see this output:
```
top
```

---

### Post by RoyalPro on 2008-04-07
This is the out of top.  The Xorg is using 91% with myth using 11% every thing else is 1% or less.

```
top - 02:16:38 up  7:15,  2 users,  load average: 1.19, 1.24, 1.08
Tasks: 145 total,   2 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6%us, 44.5%sy,  0.0%ni, 44.5%id,  2.0%wa,  0.3%hi,  1.0%si,  0.0%st
Mem:   1029092k total,   888624k used,   140468k free,    16876k buffers
Swap:  3004112k total,      180k used,  3003932k free,   475028k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5845 root      20   0  103m  27m  15m R   91  2.7 318:06.65 Xorg               
14641 marlys    20   0  624m 106m  37m S   11 10.6   2:10.55 mythfrontend.re    
14582 mythtv    20   0  466m  20m 9344 S    1  2.1   0:13.89 mythbackend        
 5895 root      20   0     0    0    0 S    1  0.0   3:10.19 lirc_pvr150        
 6402 marlys    20   0  226m  25m 9368 S    0  2.6   1:19.83 compiz.real        
    1 root      20   0  5160 1996  592 S    0  0.2   0:01.06 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.44 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.16 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.14 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.46 kblockd/0
```

---

### Post by RoyalPro on 2008-04-08
Any ideas?

---

### Post by Crafty Kisses on 2008-04-08
Have you modified your Xorg lately?

---

### Post by RoyalPro on 2008-04-08
The only changes that I have made were to the xorg.conf for the nvidia drivers.

---

### Post by jagolis on 2008-04-09
I too have this same issue in 8.04, Xorg eating a ton of CPU time on one core at a time.

Vostro 1700, 2.4ghz Core 2 Duo, 8600m GT, 3g DDR2, nvidia drivers installed via the restricted drivers manager.

It is most noteable when on the Resources tab of the System Monitor, and then general redrawing effects: e.g. menu redrawing, tab switching, etc.

I do have it installed on an NTFS partition using the Windows installer, which hopefully shouldn't matter...

---

### Post by RoyalPro on 2008-04-09
Well then I am thinking it is an Xorg problem only.  You are using different drivers, different file system, and different programs and getting the same problem with Xorg.  I really hate for my MythTV system that used to run MythTV with live recording going and a background recording going and the system sitting at a nice 35C at 1GHz.  Now I just have the live tv going and it is at 50C at the full 2.2.  I don't have the best cooling in the system because I wanted it quiet and cheap.

---

### Post by ScorpKing on 2008-04-09
when i run superkaramba on my box this happens to me. it could also be the screensaver if you use it. not sure what else

---

### Post by RoyalPro on 2008-04-10
Screen saver is set to disabled.

---

### Post by WilDCarD418 on 2008-05-15
Has anyone figured this out yet? I'm having the exact same issue described here. It makes for a rather unpleasant TV watching experience.

---

### Post by RoyalPro on 2008-05-16
I still haven't.

---

### Post by jagolis on 2008-06-12
I booted up a few days ago, and it had fixed itself. It could have been an update, but I'm not sure which one.

---

### Post by RoyalPro on 2008-06-12
looking now it looks like Xorg is now using about 2% with mythtv using about 45% guess that is better.

---

### Post by sc0g on 2008-06-20
Has anyone made any progress on this? I am looking for a fix as well but can't seem to find any. Also, I find it interesting that as I am doing an apt-get upgrade on my 8.04 Kubuntu right now, it is updating mythtv packages... HMM

Anyways, XPS400, Pentium4 2.8ghz Dual Core, 3GB RAM, blah blah pleanty of horse power basically. here's my top.

```

Tasks: 131 total,   2 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s): 60.2%us,  2.5%sy,  0.0%ni, 37.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3114624k total,   877624k used,  2237000k free,    16736k buffers
Swap:  1951856k total,        0k used,  1951856k free,   480364k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5430 root      20   0  308m 155m  47m R   93  5.1   0:49.32 Xorg
 6721 dscogin   20   0  327m 185m  67m S   27  6.1   0:23.97 mythfrontend.re
 6002 mythtv    20   0  234m  36m 9976 S    1  1.2   0:02.09 mythbackend
    1 root      20   0  2844 1688  544 S    0  0.1   0:02.02 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1

```

Granted I'm using an HDTV Tuner (AverMedia MCE A180), Xorg shouldn't be freaking out like this.

---

### Post by Jeanpaul145 on 2008-06-22
I have the exact same problem. Intel C2D T7500, latest EnvyNG nvidia driver (169.12), and I'm running Hardy x86.

```

top - 16:10:04 up 1 day, 13:00,  2 users,  load average: 1.66, 1.24, 0.77
Tasks: 144 total,   3 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s): 49.6%us,  0.2%sy,  0.0%ni, 47.8%id,  0.0%wa,  0.2%hi,  2.3%si,  0.0%st
Mem:   2074152k total,  1828996k used,   245156k free,    81728k buffers
Swap:   985376k total,    38036k used,   947340k free,  1333888k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                           
 1279 root      20   0  341m  41m 9340 R  100  2.0   2:16.94 Xorg                                                                                                                                              
 1740 j         20   0  343m  73m  23m S    1  3.6   0:10.72 firefox                                                                                                                                           
 1568 j         20   0 20952 8380 7072 S    1  0.4   0:00.58 multiload-apple                                                                                                                                   
 5129 messageb  20   0  3136 1620  796 S    0  0.1   1:22.11 dbus-daemon                                                                                                                                       
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.26 init                                                                                                                                              
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                          
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.68 migration/0                                                                                                                                       
    4 root      15  -5     0    0    0 S    0  0.0   0:03.26 ksoftirqd/0                                                                                                                                       
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                        
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.20 migration/1                                                                                                                                       
    7 root      15  -5     0    0    0 S    0  0.0   0:00.56 ksoftirqd/1                                                                                                                                       
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                        
    9 root      15  -5     0    0    0 S    0  0.0   0:01.50 events/0                                                                                                                                          
   10 root      15  -5     0    0    0 S    0  0.0   0:01.24 events/1                                                                                                                                          
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                           
   46 root      15  -5     0    0    0 S    0  0.0   0:00.16 kblockd/0                                                                                                                                         
   47 root      15  -5     0    0    0 S    0  0.0   0:00.14 kblockd/1                                                                                                                                         
   50 root      15  -5     0    0    0 S    0  0.0  15:52.81 kacpid                                                                                                                                            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                      
  154 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                                           
  197 root      20   0     0    0    0 S    0  0.0   0:02.50 pdflush                                                                                                                                           
  198 root      15  -5     0    0    0 S    0  0.0   0:00.60 kswapd0                                                                                                                                           
  239 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                             
  240 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                             
 1272 root      20   0 14692 3160 2204 S    0  0.2   0:00.02 gdm                                                                                                                                               
 1314 j         20   0 14340 2048 1648 S    0  0.1   0:00.00 gnome-keyring-d                                                                                                                                   
 1316 j         20   0 28872 7504 6296 S    0  0.4   0:00.08 x-session-manag                                                                                                                                   
 1368 j         20   0 23060 6812 4872 S    0  0.3   0:00.08 seahorse-agent                                                                                                                                    
 1374 j         20   0  2692 1088  740 S    0  0.1   0:00.06 dbus-daemon                                                                                                                                       
 1375 j         20   0 39964   9m 7892 S    0  0.5   0:00.24 gnome-settings-                                                                                                                                   
 1381 j         20   0 28472 5788 3340 S    0  0.3   0:00.07 pulseaudio                                                                                                                                        
 1384 j         20   0  5776 2248 1836 S    0  0.1   0:00.00 gconf-helper                                                                                                                                      
 1397 j         20   0  1772  536  436 S    0  0.0   0:00.00 compiz                                                                                                                                            
 1398 j         20   0 15216 2620 1728 S    0  0.1   0:00.18 gnome-screensav                                                                                                                                   
 1399 j         20   0  208m  26m  14m S    0  1.3   0:01.37 gnome-panel                                                                                                                                       
 1401 j         20   0  219m  25m  13m S    0  1.3   0:01.14 nautilus                                                                                                                                          
 1408 j         20   0 41152 3224 2424 S    0  0.2   0:00.09 bonobo-activati                                                                                                                                   
 1412 j         20   0  5372 2080 1788 S    0  0.1   0:00.00 gvfsd                                                                                                                                             
 1448 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                                     
 1449 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                                             
 1466 j         20   0 39552  28m 9428 S    0  1.4   0:01.46 compiz.real                                                                                                                                       
 1467 j         20   0 14616 5736 4836 S    0  0.3   0:00.04 bluetooth-apple                                                                                                                                   
 1469 j         20   0  176m  13m 8920 S    0  0.6   0:00.26 update-notifier                                                                                                                                   
 1472 j         20   0  207m  25m  14m S    0  1.3   0:01.30 pidgin                                                                                                                                            
 1474 j         20   0  182m  13m 8028 S    0  0.7   0:00.74 transmission                                                                                                                                      
 1477 j         20   0  177m  14m 8820 S    0  0.7   0:00.20 fusion-icon                                                                                                                                       
 1481 j         20   0 20636  11m 7388 S    0  0.6   0:11.36 cairo-clock                                                                                                                                       
 1484 j         20   0  174m  10m 8008 S    0  0.5   0:00.26 nm-applet                     

```

Something to mention: when I have Xgl installed, framerate is smooth as silk. But I don't really want to have Xgl installed because  can't play any OpenGL-accelerated games, and the temperature sensor on the gfx card don't send any info any more.

---

### Post by RoyalPro on 2008-06-23
After updates and updates one of them has got it back to where is was before.  I haven't don't a reboot like it tells me to do now after some of the updates but it has been running well with no problems for a few weeks nows and I don't plan on rebooting until I have to.  If the same problem comes up again after I get it setup with the kernel update and the like that need to be rebooted, I will let you know either way.

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2092 marlys    20   0  758m 259m  38m S   12 25.8 684:05.90 mythfrontend.re
 5969 root      20   0  113m  26m  13m S    2  2.6  55027:18 Xorg
15771 mythtv    30  10  533m  39m 9716 S    1  4.0 208:35.81 mythbackend
 6506 marlys    20   0  199m  13m 8432 S    0  1.4  29:55.79 nm-applet
    1 root      20   0  4016  828  556 S    0  0.1   0:17.60 init
```

---

### Post by Unix_Slayer on 2008-06-23
> **Jeanpaul145 said:**
> I have the exact same problem. Intel C2D T7500, latest EnvyNG nvidia driver (169.12), and I'm running Hardy x86.



Something to mention: when I have Xgl installed, framerate is smooth as silk. But I don't really want to have Xgl installed because  can't play any OpenGL-accelerated games, and the temperature sensor on the gfx card don't send any info any more.

Which NVidia card are you using?

---

### Post by Jeanpaul145 on 2008-06-23
> **Unix_Slayer said:**
> Which NVidia card are you using?

A GeForce 8600M with 512MB dedicated RAM. More than enough horses, if you ask me :popcorn:

---

### Post by RoyalPro on 2008-06-24
Back up to 65% of one core for Xorg after I did a reboot.  Wish I didn't have to do that and now I have to get my lirc working with my remote again too.  Ahhh

---

