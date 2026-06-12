---
title: "Ubuntu 12.04 unbearably slow"
date: 2014-01-29
forum: General Help
---

### Post by p.callan on 2014-01-29
I am finally getting used to using 12.04 from WinXP, meaning I can use it for everyday stuff and am learning new things every day. Frustration levels pertaining to usability have definately dropped, however 12.04 has always been laggy/slow even when I'm not really doing anything (no programs opened). I got a cpu/memory/LAN monitor and found that CPU is running at almost 100% pretty much all the time. RAM was used almost 100% as well by system processes. I had to do something about this so I started to implement the suggestions that are recommended here:
[URL="http://ubuntuhirek.wordpress.com/2012/11/22/11-tips-to-speed-up-computers-running-ubuntu-12-1012-04linux-mint-13-maya/"]
http://ubuntuhirek.wordpress.com/2012/11/22/11-tips-to-speed-up-computers-running-ubuntu-12-1012-04linux-mint-13-maya/[/URL]
[COLOR=#444444][/COLOR]
I did step 1 & 2 and on step 3 I disabled BOINC (which has been causing crashes when comp reboots from nowhere and the last thing I see is something about BOINC). Doing this completely solved the crashes. I did not uncheck any other processes but checked 'enable encryption' because every time I boot ubuntu there is an error message that "cryptswap is not ready yet" and I thought this might solve it...
Step 4 done as recommended. 
Step 5 skipped.
Step 6 skipped.
Step 7 as recommended. This lowered RAM usage dramatically.
Step 8 skipped.
Step 9 Installed this program but then it was impossible to even move the mouse. CPU at 100% and then ubuntu crashed. There was some mention of a problem on the black screen there, but it didn't stay long enough for me to read it. After reboot the OS was in the same state- CPU at 100% and every move of the mouse takes forever.
Step >9 not implemented.

I know it stings, but thanks to my dual boot of WinXP I am able to tell about this. 
I'd paste some kind of log if you tell me where to find it and how to do it. How do I copy a log from Ubuntu and move it to WinXP so that I can paste it here?

I'm like a deer in the headlights here. I'd like to get it to run smoothly (I have made only very few installations of my own and the OS-installation is very new. I don't care much for all the graphical bells and whistles, but would rather optimize for better performance if I knew how) but I am a complete noob at ubuntu. I love Ubuntu when it works, but I hate that whenever something goes wrong I have to spend weeks trying to figure out what is happening... I'm a user, not a developer. So, I care more that it *does* work, not so much about *how* it works.

My specs:
Asus eee Seashell 1015PX
Intel Atom N570 @ 1,66Ghz
2GB RAM @ 982Mhz
Ubuntu 12.04


Anyway, If you have any clue about how to help with this I am very thankful. I don't want to give up on Ubuntu now that I was finally getting into it.

Thanks.

---

### Post by TheFu on 2014-01-29
I didn't read the link.

Stock Ubuntu Desktop is GUI heavy these days with the belief that every one is running with a $300 video card.
You and I know that IS-NOT-THE-SITUATION.

Want a faster system?
#1 - stop using Unity. It is a hog.
#2 - use a different DE like LXDE or XFCE - might be easiest to just install xubuntu 12.04, though installing xfce is fairly trivial.
#3 - disable all the phone-the-mothership tracking built into new versions of Ubuntu (Amazon ads, etc.)  Fortunately, 12.04 doesn't have those, but every newer release does.

Definitely DO NOT install or update to a newer release - at least until May, then 14.04 will be ready for people like us.

Your box should be able to run x-ubuntu nicely, provided you turn down the GUI stuff OR you can install the graphics drivers for your specific GPU. I don't think Unity will ever work well on your box. It doesn't on mine.

I have an Asus Eee N280 and it works fine, but I load Ubuntu Server, then added LXDE over that.  Can't recommend the process for someone new to Linux however.  Especially for anyone needing a point-n-click solution.

---

### Post by philinux on 2014-01-29
I have an acer 1410 Intel® Celeron(R) CPU 743 @ 1.30GHz  and Mobile Intel® GM45 Express Chipset which runs Unity just fine (ubuntu 13.10). As can be seen from this Conky screenshot. 
@p.callan run the command top from a terminal. Let us know what is hogging cpu.

---

### Post by buzzingrobot on 2014-01-29
Running the System Monitor will tell you what processes are taking 100% of CPU. While an Atom 1.66 is certainly not a high-end machine, a stock Ubuntu install does not peg the CPU.

If you see errors from cryptswap, did you opt to encrypt /home? Perhaps the initial encryption has not completed or has gone awry.  (Running initial encryption on a partition will boost CPU usage until it's completed.)

I strongly disagree with suggestions to alter swappiness in an effort to speed things up by preventing the use of the swap partition. Swap exists to provide, in effect, virtual RAM when processes need more memory than is physically available. It's a fundamental component of Unix/Linux and software is written on the assumption that it is there to be used.  Yes, it takes time to write something out to swap and read it back in later.  But, something has to give when processes need more than available RAM.  If you don't allow swap to be used. there's no "give" available. In machines with a lot of RAM, swap will not see much use.  In a 2-gig machine, it just might.

Startup programs and services should not be disabled unless you are certain they do not provide an essential function.

Preload caches -- stores in memory -- components of frequently used programs so they launch faster. Simply leaving programs open is even faster, and doesn't require using the extra space.

Unity requires Compiz, but not CCSM.  Playing with CCSM settings is risky unless you know exactly what setting affect Unity and which do not.

I find the current version, 13.10, is faster with Unity than 12.04.

So-called lighter-weight versions of Ubuntu certainly exist, and might be a better fit for your hardware. However, those savings will come primarily from their use of applications with smaller memory footprints. The kernel and the essential libraries are the same on all Ubuntu versions, and, for teh most part, across all Linux distribution of similar vintage.

---

### Post by p.callan on 2014-01-30
Well now! I log into Ubuntu today and CPU is almost flatlined... I have no idea what happened but something is working right. The name of the program I monitor these with is called System Load Indicator.

> I didn't read the link.
*Stock Ubuntu Desktop is GUI heavy these days with the belief that every one is running with a $300 video card.*
*You and I know that IS-NOT-THE-SITUATION.*

*Want a faster system?*
*#1 - stop using Unity. It is a hog.*
*#2 - use a different DE like LXDE or XFCE - might be easiest to just install xubuntu 12.04, though installing xfce is fairly trivial.*
[I]#3 - disable all the phone-the-mothership tracking built into new versions of Ubuntu (Amazon ads, etc.) Fortunately, 12.04 doesn't have those, but every newer release does.
[/I]**- #1 & #2 yeah, this is what I am talking about. With Ubuntu I have to spend days trying to find out what all the abbreviations mean and entail before I can even begin to consider LEARNING how to install one or the other, which takes even more time. I hear you on #3 though, that's the first thing I did after OS install =)**

*Definitely DO NOT install or update to a newer release - at least until May, then 14.04 will be ready for people like us. ***What I was thinking too. I chose the LTS for a good reason.**
*Your box should be able to run x-ubuntu nicely, provided you turn down the GUI stuff OR you can install the graphics drivers for your specific GPU. I don't think Unity will ever work well on your box. It doesn't on mine.*
[I]I have an Asus Eee N280 and it works fine, but I load Ubuntu Server, then added LXDE over that. Can't recommend the process for someone new to Linux however. Especially for anyone needing a point-n-click solution.
[/I]**Yeah, maybe Xubuntu in the future, when I have time to look into it all.**



> @p.callan run the command top from a terminal. Let us know what is hogging cpu.
Ok, there doesn't seem to be a hog now though...


top - 17:05:45 up 31 min,  2 users,  load average: 0.61, 0.70, 0.69
Tasks: 182 total,   1 running, 181 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.1%us,  3.6%sy,  0.0%ni, 79.9%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2055088k total,  1292476k used,   762612k free,    97760k buffers
Swap:  3109324k total,        0k used,  3109324k free,   834760k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                   
 2044 username   20   0  360m  59m  26m S   30  3.0   5:18.13 compiz                                    
 2143 username   20   0 93980  16m  10m S   13  0.8   3:31.36 unity-panel-ser                           
 1127 root      20   0 80848  16m 7876 S   12  0.8   1:31.82 Xorg                                      
 2812 username   20   0 92896  14m  10m S    8  0.7   0:02.09 gnome-terminal                            
 2146 username   20   0 67224 5868 3280 S    7  0.3   1:47.84 hud-service                               
 2262 username   20   0 49388 9124 7104 S    5  0.4   1:26.72 indicator-multi                           
 2335 username   20   0  295m  99m  32m S    5  4.9   1:53.63 midori                                    
 2016 username   20   0  6516 2696  640 S    4  0.1   0:57.68 dbus-daemon                               
 2171 username   20   0 64640 4448 3616 S    3  0.2   0:40.44 indicator-appli                           
 2024 username   20   0  135m  15m  11m S    1  0.8   0:04.62 gnome-settings-                           
 2877 username   20   0  2852 1196  896 R    1  0.1   0:00.67 top                                       
   10 root      20   0     0    0    0 S    1  0.0   0:07.46 rcu_sched                                 
 2229 username   20   0 41240   9m 8212 S    1  0.5   0:02.32 gtk-window-deco                           
   23 root      20   0     0    0    0 S    0  0.0   0:03.16 ksoftirqd/3                               
   40 root      20   0     0    0    0 S    0  0.0   0:04.04 kworker/2:1                               
   41 root      20   0     0    0    0 S    0  0.0   0:02.60 kworker/3:1                               
   64 root      20   0     0    0    0 S    0  0.0   0:01.97 kworker/u:3                               
 1074 root      20   0 31192 5092 4232 S    0  0.2   0:01.18 NetworkManager                            
 2123 username   20   0 49584 8796 6912 S    0  0.4   0:10.50 bamfdaemon                                
    1 root      20   0  3792 2204 1360 S    0  0.1   0:02.44 init                                      
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                  
    3 root      20   0     0    0    0 S    0  0.0   0:03.14 ksoftirqd/0                               
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:0                               
    5 root       0 -20     0    0    0 S    0  0.0   0:00.00 kworker/0:0H                              
    7 root       0 -20     0    0    0 S    0  0.0   0:00.00 kworker/u:0H                              
    8 root      RT   0     0    0    0 S    0  0.0   0:00.41 migration/0                               
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 rcu_bh                                    
   11 root      RT   0     0    0    0 S    0  0.0   0:00.02 watchdog/0                                
   12 root      RT   0     0    0    0 S    0  0.0   0:00.02 watchdog/1                                
   13 root      20   0     0    0    0 S    0  0.0   0:03.07 ksoftirqd/1                               
   14 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/1                               
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0                               
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 kworker/1:0H                              
   17 root      RT   0     0    0    0 S    0  0.0   0:00.02 watchdog/2                                
   18 root      20   0     0    0    0 S    0  0.0   0:02.73 ksoftirqd/2                               
   19 root      RT   0     0    0    0 S    0  0.0   0:00.33 migration/2                               
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 kworker/2:0H                              
   22 root      RT   0     0    0    0 S    0  0.0   0:00.01 watchdog/3                                
   24 root      RT   0     0    0    0 S    0  0.0   0:00.06 migration/3 




> Running the System Monitor will tell you what processes are taking 100% of CPU. While an Atom 1.66 is certainly not a high-end machine, a stock Ubuntu install does not peg the CPU.
If you see errors from cryptswap, did you opt to encrypt /home? Perhaps the initial encryption has not completed or has gone awry. (Running initial encryption on a partition will boost CPU usage until it's completed.)
**Yes, I did choose that. On an earlier installation of ubuntu I found a solution for this problem online, but now I can't find it again. I don't think it's an installation error as it happened twice.**


I strongly disagree with suggestions to alter swappiness in an effort to speed things up by preventing the use of the swap partition. Swap exists to provide, in effect, virtual RAM when processes need more memory than is physically available. It's a fundamental component of Unix/Linux and software is written on the assumption that it is there to be used. Yes, it takes time to write something out to swap and read it back in later. But, something has to give when processes need more than available RAM. If you don't allow swap to be used. there's no "give" available. In machines with a lot of RAM, swap will not see much use. In a 2-gig machine, it just might.
**I thought the space on the HDD, the swap, was beyond the RAM, meaning there's still 100% of RAM available?**


Startup programs and services should not be disabled unless you are certain they do not provide an essential function.
**Yeah, same in Win. Only disabled BOINC. Strange thing is that now I can't uninstall it for some reason (via uSWC).**


Preload caches -- stores in memory -- components of frequently used programs so they launch faster. Simply leaving programs open is even faster, and doesn't require using the extra space.
**Ok, well I found that leaving programs open and then switching between them (alt+tab) takes a looooooong time. She doesn't like that at all (Charlene, my computer).**


Unity requires Compiz, but not CCSM. Playing with CCSM settings is risky unless you know exactly what setting affect Unity and which do not.
I find the current version, 13.10, is faster with Unity than 12.04.


So-called lighter-weight versions of Ubuntu certainly exist, and might be a better fit for your hardware. However, those savings will come primarily from their use of applications with smaller memory footprints. The kernel and the essential libraries are the same on all Ubuntu versions, and, for teh most part, across all Linux distribution of similar vintage.
**Ok, well maybe 14.04 will be worth a try when the time comes.**


---

### Post by philinux on 2014-01-30
If it happens again run top straight away to nail the culprit software.

---

### Post by TheFu on 2014-01-30
```
2044 username   20   0  360m  59m  26m S   30  3.0   5:18.13 compiz
```
30% for a compositor!!!!!!   THAT is an issue IMHO.

Guess that I'm alone in this way of thinking.  I would **sudo aptitude purge compiz** and be done with this issue.
Compiz is NOT needed.

---

### Post by philinux on 2014-01-30
Unity is a compiz plugin. Removing it would bork the system. It might have just been a spike.

---

### Post by TheFu on 2014-01-30
> **philinux said:**
> Unity is a compiz plugin. Removing it would bork the system. It might have just been a spike.

I have a running 12.04 box.  Did this a few minutes ago:
```
$ sudo aptitude purge compiz 
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  compiz* unity*
0 upgraded, 0 newly installed, 2 to remove and 8 not upgraded.
After this operation, 3,703 kB disk space will be freed.
(Reading database ... 50%Y/n]? y 
(Reading database ... 
(Reading database ... 270790 files and directories currently inst
lled.)
Removing unity ...
Removing compiz ...
Processing triggers for man-db ...
```

Rebooted, picked Unity2D from the login menu and logged in just fine.  Not seeing any negative effects. 
Was it just luck on my system?

---

### Post by philinux on 2014-01-30
Ah yes unity2d does not use compiz. No effects at all. The trade off is a lack of any customisation like launcher icon size etc. 

12.04 LTS is also using and older more resource intensive version of unity. I'm on 13.10 on an acer 1410 and not seeing any ill effects of using unity 3d.

---

