---
title: "system suddenly very slow"
date: 2015-04-27
forum: General Help
---

### Post by vilwarin on 2015-04-27
Dear forum,

since 2-3 weeks ago I noticed my system getting very slow. Especially when watching videos, but also just using firefox and thunderbird.
I used to play games like Wesnoth, this is no longer possible at the moment.

Some Details:
compaq laptop
Ubuntu 14.04
NVIDIA GeForce 820M (nvidia-311, nvidia-prime; set to always use the nvidia card)
4 CPUs
4 GB RAM

I first suspected the flash-plugin, since I noticed that watching videos suddenly caused severe problems. But since it also occurs when no flash application is running, this can't be the cause.
I then suspected the graphics card. But glx-gears is, while visible slow, giving ok results of 2500-3000 FPS in 5 minutes (unfortunately I have no values from before to compare).
Even more strange. When the system gets this slow and I check "top", I see no load that would explain the slow behaviour.

Do you have any ideas, what I could check next? 
I'm at my wits end :)

Thanks!,

vilwarin

---

### Post by ian-weisser on 2015-04-28
Open a terminal when things are running smoothly.

When things start to run sloooowwwwly, click into the open terminal window.
1) Run the 'free' command. It will tell you if your RAM is full.
2) Run the 'top' command. It will tell you the greatest resource-consuming processes. ('q' to quit)

If you have any questions about the output, copy-and-paste the output here.

---

### Post by vilwarin on 2015-04-29
here's the results, when running a game (System Shock 2).
I played that game a few months ago without any problem, now everything is too slow and laggy to do anything in the game.

$free
             total       used       free     shared    buffers     cached
Mem:       3937700    3806064     131636     248964     207104     887636
-/+ buffers/cache:    2711324    1226376
Swap:      7810044       8736    7801308

$top

top - 07:55:12 up 29 min,  5 users,  load average: 1,95, 1,97, 1,61
Tasks: 260 total,   3 running, 256 sleeping,   0 stopped,   1 zombie
%Cpu(s): 39,2 us, 14,2 sy,  0,0 ni, 45,8 id,  0,5 wa,  0,0 hi,  0,3 si,  0,0 st
KiB Mem:   3937700 total,  3800040 used,   137660 free,   194832 buffers
KiB Swap:  7810044 total,    13644 used,  7796400 free.   868400 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 8967 vilwarin   20   0 2981120 211340  75944 R 152,2  5,4   3:34.66 Shock2.exe  
 8943 vilwarin   20   0   66896  32984   6392 R  20,9  0,8   0:40.45 wineserver  
 4984 vilwarin   20   0 1652940 208048  72480 S   8,6  5,3   1:41.12 compiz      
 3529 root      20   0  456200 246908  55936 S   6,6  6,3   4:45.96 Xorg

---

### Post by ian-weisser on 2015-04-29
Er, please use [code] tags when posting output. It keeps the formatting, which is helpful.

> **vilwarin said:**
> total       used       free     shared    buffers     cached
Mem:       **3937700    3806064**     131636     248964     207104     887636
-/+ buffers/cache:    2711324    1226376
Swap:      7810044       **8736**    7801308

Your RAM is full: 3.8M used out of 3.9M available, and you're starting to use swap...which is *much* slower.


> **vilwarin said:**
> top - 07:55:12 up 29 min,  **5 users**,  load average: 1,95, 1,97, 1,61
Tasks: **260 total**,   3 running, 256 sleeping,   0 stopped,   **1 zombie**
%Cpu(s): **39,2 **us, 14,2 sy,  0,0 ni, **45,8** id,  0,5 wa,  0,0 hi,  0,3 si,  0,0 st
KiB Mem:   3937700 total,  3800040 used,   137660 free,   194832 buffers
KiB Swap:  7810044 total,    13644 used,  7796400 free.   868400 cached Mem

You seem to have a lot of users logged in (5 instead of perhaps 2).
Your number of tasks seems a bit high to me (260 instead of perhaps 200). Perhaps you have applications sleeping in the background?
A zombie process is always troubling. 
Your CPU seems to have plenty of idle time available.


> **vilwarin said:**
> PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 8967 vilwarin   20   0 2981120 211340  75944 R **152,2  5,4**   3:34.66 Shock2.exe  
 8943 vilwarin   20   0   66896  32984   6392 R  **20,9  0,8**   0:40.45 wineserver  
 4984 vilwarin   20   0 1652940 208048  72480 S   **8,6  5,3**   1:41.12 compiz      
 3529 root      20   0  456200 246908  55936 S **  6,6  6,3**   4:45.96 Xorg

This looks expected. Shock2 consumes only 5.4% of memory. All your active tasks consume less than 20% of your RAM.
Yet your RAM is full, and memory demand is spilling over into swap.

The easy way to fix the problem is to simply reboot. That should clean out the excess processes, the zombie, the extra users, and other memory hogs. It should also free the memory.

If you discover one process that consumes lots of memory, bit does not free it again when finished, please file a bug report. Processes are not supposed to leak memory like that.

---

### Post by vilwarin on 2015-04-29
Hi ian-weisser,

thanks for your thoughts, I think we are getting somewhere.

>  The easy way to fix the problem is to simply reboot. That should clean out the excess processes, the zombie, the extra users, and other memory hogs. It should also free the memory.
I did the above test this morning directly after starting up my Laptop (HP Compaq 15-h023).
So rebooting isn't really an option as I performed the test basically in a freshly booted state.

>  If you discover one process that consumes lots of memory, bit does not free it again when finished, please file a bug report. Processes are not supposed to leak memory like that.
Watching the memory consumption, the process taking the most memory is firefox. It is listed a lot of times, but looking at the total consumption, the values don't add up. So I guess it's one time 14%

```
top - 15:04:07 up 21 min,  4 users,  load average: 0,18, 0,30, 0,31
Tasks: 236 total,   1 running, 235 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0,5 us,  0,3 sy,  0,0 ni, 99,2 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:   3937700 total,  2765716 used,  1171984 free,   123984 buffers
KiB Swap:  7810044 total,        0 used,  7810044 free.  1240544 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                           
 4467 michael   20   0 1507188 565056  57396 S   0,7 14,3   1:37.33 firefox                           
 5466 michael   20   0 2385328 129052  61932 S   0,0  3,3   0:02.18 python                            
 4406 michael   20   0 1561572 114060  60196 S   0,0  2,9   0:13.20 compiz                            
 4977 michael   20   0 2753516 100248  29668 S   0,0  2,5   0:06.22 dropbox                           
 2861 root      20   0  273376  89344  44244 S   2,3  2,3   0:33.28 Xorg                              
 4353 michael   20   0 1077520  47996   7788 S   0,0  1,2   0:00.29 evolution-calen                   
 4119 michael   20   0  762480  47440  29288 S   0,0  1,2   0:00.63 hud-service                       
 4448 michael   20   0 1608380  40396  28988 S   0,3  1,0   0:02.12 nautilus                          
 4523 michael   20   0  496420  36900  13984 S   0,0  0,9   0:01.84 my-weather-indi                   
 2003 debian-+  20   0   65076  31600   9708 S   0,0  0,8   0:02.69 tor                               
 4424 michael   20   0  838688  30908  12348 S   0,3  0,8   0:04.24 autokey-gtk                       
 4113 michael   20   0  743992  26488  12832 S   0,0  0,7   0:00.91 unity-settings-                   
 4131 michael   20   0  581448  25384  12940 S   0,3  0,6   0:02.61 unity-panel-ser                   
 8065 michael   20   0  736504  22476  14112 S   1,3  0,6   0:02.37 gnome-terminal                    
 4417 michael   20   0  435748  19936  10336 S   0,0  0,5   0:00.18 python                            
 4461 michael   20   0  751952  19812  13648 S   0,0  0,5   0:01.05 nm-applet   

```

> You seem to have a lot of users logged in (5 instead of perhaps 2).
Thanks for noticing the five users. I wonder where they come from?
```
$users
michael michael michael michael

```
It seems I am being looged in multiple times? Very odd.
Have you seen this behaviour in Ubuntu before?

Who shows
```
$who
michael  tty1         2015-04-29 14:45
michael  :0           2015-04-29 14:45 (:0)
michael  pts/6        2015-04-29 14:57 (:0)
michael  pts/10       2015-04-29 15:00 (:0)

```
I boot in a shell first, from there I start lightdm. So that explains two users, I guess?

> Your number of tasks seems a bit high to me (260 instead of perhaps 200). Perhaps you have applications sleeping in the background?
A zombie process is always troubling. 
Any tip on how to find the sleeping processes? They must start automatically after booting, as I performed the test right after boot.
I'll google and check what a zombie process is. I don't have one at this moment.

Any further ideas are very welcome :)

Michael

---

### Post by ian-weisser on 2015-04-29
See the difference in memory the second time:

> **vilwarin said:**
> ```
top - 15:04:07 up 21 min,  4 users,  load average: 0,18, 0,30, 0,31
Tasks: 236 total,   1 running, 235 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0,5 us,  0,3 sy,  0,0 ni, 99,2 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:   **3937700** total,  **2765716** used,  **1171984** free,   123984 buffers
KiB Swap:  7810044 total,        **0 **used,  7810044 free.  1240544 cached Mem
```

2.7M used, 1.2M free, no swap used. Plenty of memory available. Looks much more normal. Was your system faster and more responsive?
If so, then checking your memory usage before starting a game might be a simple way to prevent slowdowns.

> **vilwarin said:**
>  ```
$who
michael  tty1         2015-04-29 14:45
michael  :0           2015-04-29 14:45 (:0)
michael  pts/6        2015-04-29 14:57 (:0)
michael  pts/10       2015-04-29 15:00 (:0)

```
I boot in a shell first, from there I start lightdm. So that explains two users, I guess?

Yes, that would explain it.
tty1 is the console
:0 is the lighdm login
pts/ are the terminal windows

---

### Post by vilwarin on 2015-04-30
> 2.7M used, 1.2M free, no swap used. Plenty of memory available. Looks much more normal. Was your system faster and more responsive?

Yes it was more responsive.
Starting a video or game, my system gets unresponsive within a couple of minutes. 
Without video or game, my system gets unresponsive within a couple of hours. 

The thing is, I'd like to watch a video now and then ;). And since it worked smoothly before, I know there must be a cause to the sudden drop in performance.

> If so, then checking your memory usage before starting a game might be a simple way to prevent slowdowns.
Unfortunately that doesn't help. Like I said, even in a freshly booted state with almost all memory still free my system clogs within a few minutes when starting a game or video.

---

### Post by ian-weisser on 2015-04-30
The something you are running seems to have quite a memory leak.
If you can identify which process is the culprit, and identify a reliable way to reproduce the leak, please file a bug report.
Developers are generally happy to fix memory leaks when they can find them.

---

### Post by vilwarin on 2015-05-01
Hey ian,

thanks, I think that's a viable strategy.
Can you tell me a good way to find memory leaking processes?

---

### Post by ian-weisser on 2015-05-01
See [http://stackoverflow.com/questions/143791/how-do-i-find-which-process-is-leaking-memory](http://stackoverflow.com/questions/143791/how-do-i-find-which-process-is-leaking-memory) for several good ways.

---

