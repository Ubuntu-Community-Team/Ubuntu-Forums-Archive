---
title: "Very High Memory Usage In 14.10"
date: 2014-11-16
forum: General Help
---

### Post by typos1 on 2014-11-16
Since upgrading with no apps running memory usage is 50-60%, if I open Firefox and Thunderbird, it goes up to 90%, running SMplayer makes it go up to 97% !! 

I ve searched for anything that shows particularly high memory use but I cant really see anything that sticks out, I didnt have this problem with 14.04.

Any suggestions ?

Thanks

---

### Post by Doug S on 2014-11-16
Review [this thread]("http://ubuntuforums.org/showthread.php?t=2244787"), maybe it will address your concerns. If not, post back and we'll go from there.

---

### Post by typos1 on 2014-11-16
Thanks, but thats no help I m going by the mem usage in the system monitor applet at the top of the screen and its been very high since upgrading to 14.10, like I said 50-60% whilst doing nothing, it wasnt like this in 14.04.

---

### Post by Doug S on 2014-11-16
> **typos1 said:**
> Thanks, but thats no help I m going by the mem usage in the system monitor applet at the top of the screen and its been very high since upgrading to 14.10, like I said 50-60% whilst doing nothing, it wasnt like this in 14.04.Then I am unable to help, as I do not use any system monitor applet. Perhaps someone else will chime in. The thread I referred to does use more primitive commands, but the answers should be the same.

---

### Post by sammiev on 2014-11-16
Try installing htop and see what your load is.

---

### Post by typos1 on 2014-11-17
> **Doug S said:**
> Then I am unable to help, as I do not use any system monitor applet. Perhaps someone else will chime in. The thread I referred to does use more primitive commands, but the answers should be the same.

The applet is just a plugin for system monitor, it takes its info from there.

> **sammiev said:**
> Try installing htop and see what your load is.

Thanks, but I can use the terminal, no need for a guide and I know what my load is, its 50-60%, I need help finding out why it is so high and stopping it.

I ve installed htop and it tells me hat I already know - that memory load is 50-60% !!

---

### Post by Impavidus on 2014-11-17
Maybe the system monitor applet changed between release 14.04 and 14.10. It would be nice to see some more details. The **free** tool can provide these:```
free -m
```Is your system slowing down because it uses swap? Or are applications getting killed because they run out of memory? If not, there is nothing to worry about. Unused memory is wasted memory.

Maybe the applet includes the cache.

---

### Post by typos1 on 2014-11-17
> **Impavidus said:**
> Maybe the system monitor applet changed between release 14.04 and 14.10. It would be nice to see some more details. The **free** tool can provide these:```
free -m
```Is your system slowing down because it uses swap? Or are applications getting killed because they run out of memory? If not, there is nothing to worry about. Unused memory is wasted memory.

Maybe the applet includes the cache.

I ve never had any problems with all the versions I ve used before, but before I posted I did come across something about swap and I reduced teh amount of swap from 60 (standard) to 30. It made no difference.

Its not just the applet, system monitor shows high use as well, I ve tried closing some apps but doesnt make much difference. I think its real high mem usage because if I use smplayer as well as firefox and thunderbird, the fan starts up and everything gets slower. 

Here is the output :


```

         free -m total       used       free     shared    buffers     cached
  Mem:            3952       3601        350        193        151       1475
  -/+ buffers/cache:       1974       1977
  Swap:          988          0        988

```

This seems to confirm that usage is high.

(Cant remember what I have to do for terminal output to be in a window, let me know and I ll edit post)

---

### Post by Impavidus on 2014-11-17
It seems you changed the swappiness from 60 to 30. That can change the amount of swap used, but shouldn't really influence the memory usage. It just waits longer before swapping and then swaps more at once.

The fan usually indicates the cpu is working hard, which also slows things down. Firefox can use a lot of cpu time if it's playing flash content. It's not directly connected to memory. You used 50% of memory there, with another 37% used for cache and buffers. You did not use swap. What did the applet say there?

You can use [noparse]```
code tags
```[/noparse] to get things in a box, like for comparison my memory usage:```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          7918       1787       6130         63        101       1017
-/+ buffers/cache:        668       7250
Swap:         8667          0       8667
```Note that I'm on Xubuntu, which uses less memory than Ubuntu.

---

### Post by typos1 on 2014-11-17
> **Impavidus said:**
> It seems you changed the swappiness from 60 to 30. That can change the amount of swap used, but shouldn't really influence the memory usage. It just waits longer before swapping and then swaps more at once.

The fan usually indicates the cpu is working hard, which also slows things down. Firefox can use a lot of cpu time if it's playing flash content. It's not directly connected to memory. You used 50% of memory there, with another 37% used for cache and buffers. You did not use swap. What did the applet say there?

You can use [noparse]```
code tags
```[/noparse] to get things in a box, like for comparison my memory usage:```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          7918       1787       6130         63        101       1017
-/+ buffers/cache:        668       7250
Swap:         8667          0       8667
```Note that I'm on Xubuntu, which uses less memory than Ubuntu.

Yes, I know I changed the swappiness from 60 to 30, thats what I said in a previous post !

I know the fan indicates that the cpu is working hard, this often also means that a lot of memory is being used, which it is. 

When doing nothing, with no apps running memory usage is 50-60 %, this is not right, my system is slow and laggy, something appears to be using a lot of memory and slowing it down. I know firefox can use a lot of memory if its playing flash and if I play flash then memory goes up to 97% !! Just like if I use smplayer as well as firefox and thunderbird.

The applet said I was using 87%, which is correct. 

I should not be using 50-60% of my memory when there are no apps running, something is wrong and I need some help finding out what.

---

### Post by Impavidus on 2014-11-18
If the applet said you were using 87% of your memory, it included the cache. Any properly caching operating system will use all available memory for cache, so memory usage including cache will always rise to 100%. As cache is dropped as soon as an application needs the memory, you can ignore it. So, you were only using 50% of memory and the applet (and system monitor) don't do a very good job.

The system shouldn't slow down significantly because of high memory usage until you start using swap. You didn't use swap when you ran **free**. If your system is slow and not using swap (you should notice the hard drive activity), check for processes using too much cpu time.

---

### Post by typos1 on 2014-11-18
> **Impavidus said:**
> If the applet said you were using 87% of your memory, it included the cache. Any properly caching operating system will use all available memory for cache, so memory usage including cache will always rise to 100%. As cache is dropped as soon as an application needs the memory, you can ignore it. So, you were only using 50% of memory and the applet (and system monitor) don't do a very good job.

The system shouldn't slow down significantly because of high memory usage until you start using swap. You didn't use swap when you ran **free**. If your system is slow and not using swap (you should notice the hard drive activity), check for processes using too much cpu time.

The first thing I did was to check for processes using cpu time, but there are none. 

None of the previous version has registered this much memory load in the 5 years I ve been using Ubuntu, 14.04 did not either, since 14.10 the applet has been reporting 50-60% mem usage doing nothing and it appears to be sctual usage, not cache because the fan kicks n and everything slows down if I use firefox, thumderbird and smplayer all at the same time, mem use goes to 97%, none of this has happened before. 

And if the applet included the cache, then why has it only started to do so since 14.10 ? It didnt do it from 8.04 through to 14.04. it would register no more than 10-15% mem usage with nothing running.

---

### Post by Doug S on 2014-11-18
Thanks for providing your output from "free -m", as indeed it seems to "actually" be using way more memory than one would expect (assuming that was doing nothing output). My free -m is more like the other poster:```
doug@desk-dev:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7984        803       7181          7         32        249
-/+ buffers/cache:        [COLOR=#ff0000]521       7463[/COLOR]
Swap:         8188          0       8188
```I still recommend (as I did on that other thread I referred to) to use top and sort by RES (Resident memory) to find the highest memory users. Here is mine:```
top - 08:38:38 up 12 min,  2 users,  load average: 0.01, 0.04, 0.05
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
%Cpu0  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu1  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu2  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu3  :  0.0 us,  0.3 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   8176068 total,   881792 used,  7294276 free,    35392 buffers
KiB Swap:  8385532 total,        0 used,  8385532 free.   303692 cached Mem

  PID USER      PR  NI    VIRT    [COLOR=#ff0000]RES[/COLOR]    SHR S  %CPU %MEM     TIME+ COMMAND
 2011 doug      20   0 1403068 [COLOR=#ff0000]177152[/COLOR]  62452 S   0.0  2.2   0:05.72 compiz
 1175 root      20   0  399320 [COLOR=#ff0000]105368[/COLOR]  23980 S   0.0  1.3   0:03.91 Xorg
 2176 doug      20   0 1074728  [COLOR=#ff0000]58884[/COLOR]  19852 S   0.0  0.7   0:00.17 evolution-calen
 2246 doug      20   0 1011712  [COLOR=#ff0000]48972[/COLOR]  39736 S   0.0  0.6   0:00.41 nautilus
 2238 doug      20   0  605968  33692  25904 S   0.0  0.4   0:00.10 nm-applet
 1997 doug      20   0  418076  31692  27604 S   0.0  0.4   0:00.08 hud-service
 2024 doug      20   0  514604  30632  23048 S   0.0  0.4   0:00.17 unity-panel-ser
 1999 doug      20   0  829968  29136  22824 S   0.0  0.4   0:00.17 unity-settings-
 1991 doug      20   0  495640  26592  21552 S   0.0  0.3   0:00.07 ibus-ui-gtk3
 2758 doug      20   0  512180  23996  20324 S   0.0  0.3   0:00.07 update-notifier
 2096 doug      20   0  740008  23844  18424 S   0.0  0.3   0:00.08 indicator-keybo
 2098 doug      20   0  463884  22660  18744 S   0.0  0.3   0:00.05 indicator-print
 2018 doug      20   0  735248  21868  18004 S   0.0  0.3   0:00.11 gnome-session
 1930 doug      20   0  502620  21424  17760 S   0.0  0.3   0:00.11 bamfdaemon
 2480 doug      20   0  464204  20972  17544 S   0.0  0.3   0:00.06 telepathy-indic
 2153 doug      20   0  532920  20960  17660 S   0.0  0.3   0:00.03 evolution-sourc
 2225 doug      20   0  354608  20484  17264 S   0.0  0.3   0:00.04 notify-osd
 2241 doug      20   0  345940  19948  16800 S   0.0  0.2   0:00.03 polkit-gnome-au
 2254 doug      20   0  415260  19456  16384 S   0.0  0.2   0:00.03 unity-fallback-
 2095 doug      20   0 1052240  19124  13684 S   0.0  0.2   0:00.06 indicator-datet
 1995 doug      20   0  388352  17276  13412 S   0.0  0.2   0:00.03 ibus-x11
 2544 doug      20   0  500280  14832  12812 S   0.0  0.2   0:00.03 zeitgeist-datah
 2487 doug      20   0  328564  13068  11652 S   0.0  0.2   0:00.03 mission-control
 1747 colord    20   0  305612  12092   7812 S   0.0  0.1   0:00.07 colord
 2097 doug      20   0  565732  11360   9604 S   0.0  0.1   0:00.03 indicator-sound
 2542 doug      20   0  233648  11164   8152 S   0.0  0.1   0:00.01 zeitgeist-fts
 2131 doug      20   0  380876  11012   9736 S   0.0  0.1   0:00.02 indicator-appli
  651 root      20   0  350828  10980   9392 S   0.0  0.1   0:00.05 NetworkManager
 1001 whoopsie  20   0  374120  10776   9280 S   0.0  0.1   0:00.02 whoopsie
  616 root      20   0  287656  10496   6216 S   0.0  0.1   0:00.16 polkitd
 1945 doug      20   0  359312   9416   6724 S   0.0  0.1   0:00.00 at-spi-bus-laun
 2092 doug      20   0  356828   9384   6672 S   0.0  0.1   0:00.00 indicator-messa
 1819 doug      20   0  390448   9132   8256 S   0.0  0.1   0:00.01 gnome-keyring-d
 1589 root      20   0  254080   8736   7548 S   0.0  0.1   0:00.02 upowerd
 2307 root      20   0  377748   8476   6872 S   0.0  0.1   0:00.02 udisksd
 2304 doug      20   0  303088   8452   7196 S   0.0  0.1   0:00.01 gvfs-udisks2-vo
 2536 doug      20   0  331576   8176   5348 S   0.0  0.1   0:00.02 zeitgeist-daemo
 1913 doug      20   0   79120   7956   7424 S   0.0  0.1   0:00.00 window-stack-br
 2900 doug      20   0  376936   7716   6860 S   0.0  0.1   0:00.02 deja-dup-monito
 1179 root      20   0  293832   7712   6648 S   0.0  0.1   0:00.10 accounts-daemon
 2099 doug      20   0  766968   7680   6624 S   0.0  0.1   0:00.03 indicator-sessi
 2339 doug      20   0  203992   7644   5004 S   0.0  0.1   0:00.00 gvfs-gphoto2-vo
 1974 doug      20   0  367952   7636   6500 S   0.0  0.1   0:00.04 ibus-daemon
 2333 doug      20   0  298592   7604   6676 S   0.0  0.1   0:00.00 gvfs-afc-volume
 1987 doug      20   0  287276   7596   6884 S   0.0  0.1   0:00.00 ibus-dconf
  600 root      20   0  328792   7576   6420 S   0.0  0.1   0:00.01 ModemManager
 2345 doug      20   0  439576   7520   6704 S   0.0  0.1   0:00.00 gvfsd-trash
```

---

### Post by typos1 on 2014-11-19
> **Doug S said:**
> Thanks for providing your output from "free -m", as indeed it seems to "actually" be using way more memory than one would expect (assuming that was doing nothing output). My free -m is more like the other poster:

Ok, the first thing I did before I even posted was to use system monitor to try and work out what process/processes was/were causing it, but it was hard to establish, top appears to be better. Using system monitor I did manage to establsih that evolution was using a lot of memory, I attempted to remove the package using synaptic bur it had other dependencies so I decided to post on here and ask.Things like unity, date-time indicator, nautilus etc also were using a lot, but for obvious reasons I didnt want to kill any of those processes and I dont ahve another system to make comparisons of memory use to see if any of those processes were using more than they should be.

When you mean sort by "RES" do just mean look at that column ? 

Its hard to read as the output in the terminal changes very second or so, but I ve managed to capture 2 outputs :

```

top - 15:43:52 up 18 min,  2 users,  load average: 0.96, 1.12, 1.06
Tasks: 201 total,   1 running, 200 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.1 us,  7.9 sy,  0.0 ni, 82.6 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4047156 total,  3040200 used,  1006956 free,   134816 buffers
KiB Swap:  1012088 total,        0 used,  1012088 free.  1279648 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 3400 user      20   0  574336  54636  42980 S  19.2  1.3   1:13.04 gnome-syst+ 
 1946 root      20   0  261704  80256  45464 S   5.3  2.0   1:04.64 Xorg        
 3094 user      20   0 1328888 450952  85084 S   5.3 11.1   4:46.14 firefox     
 2529 user      20   0 1801720 153684  75696 S   3.3  3.8   0:50.53 compiz      
 3307 user      20   0  692144  33140  25612 S   2.3  0.8   0:02.37 gnome-term+ 
 3331 user      20   0   27688   2924   2396 R   0.7  0.1   0:03.02 top         
 1964 root      20   0   59368   5228   4520 S   0.3  0.1   0:00.34 avgoad      
 3398 root      20   0       0      0      0 S   0.3  0.0   0:00.70 kworker/0:1 
 3451 root      20   0       0      0      0 S   0.3  0.0   0:00.12 kworker/0:2 
    1 root      20   0   29536   4084   2344 S   0.0  0.1   0:02.66 init        
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.05 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0.0  0.0   0:02.25 rcu_sched   
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.94 rcuos/0     
    9 root      20   0       0      0      0 S   0.0  0.0   0:01.05 rcuos/1     
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh      
   11 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0     
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1     
   13 root      rt   0       0      0      0 S   0.0  0.0   0:00.21 migration/0 
   14 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/0  
   15 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1  
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.14 migration/1 
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.03 ksoftirqd/1 
   19 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+ 
   20 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper     
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs   
   22 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns       
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd  
   24 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback   
   25 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd        
   26 root      39  19       0      0      0 S   0.0  0.0   0:00.41 khugepaged

```

```

top - 15:43:31 up 17 min,  2 users,  load average: 1.03, 1.15, 1.07
top - 15:45:11 up 19 min,  2 users,  load average: 0.71, 1.02, 1.03
Tasks: 201 total,   2 running, 199 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.2 us,  6.5 sy,  0.0 ni, 83.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4047156 total,  3048908 used,   998248 free,   134820 buffers
KiB Swap:  1012088 total,        0 used,  1012088 free.  1279676 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 3400 user      20   0  574340  54636  42980 R  17.3  1.3   1:27.79 gnome-syst+ 
 3094 user      20   0 1328856 458732  85148 S  12.9 11.3   5:01.91 firefox     
 2529 user      20   0 1801720 154112  75696 S   2.0  3.8   0:52.66 compiz      
 1946 root      20   0  261704  80256  45464 S   1.0  2.0   1:12.29 Xorg        
 1763 kernoops  20   0   35328   2596   2268 S   0.3  0.1   0:00.02 kerneloops  
 2435 user      20   0   45152   3656   2048 S   0.3  0.1   0:01.95 dbus-daemon 
 2528 user      20   0  851916  38176  25384 S   0.3  0.9   0:02.97 unity-pane+ 
 2652 user      20   0  461964  37496  24184 S   0.3  0.9   0:01.40 indicator-+ 
 2736 user      20   0  509012  33872  19468 S   0.3  0.8   0:01.51 indicator-+ 
 3307 user      20   0  692144  33352  25612 S   0.3  0.8   0:02.94 gnome-term+ 
    1 root      20   0   29536   4084   2344 S   0.0  0.1   0:02.66 init        
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.05 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0.0  0.0   0:02.35 rcu_sched   
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.98 rcuos/0     
    9 root      20   0       0      0      0 S   0.0  0.0   0:01.08 rcuos/1     
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh      
   11 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0     
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1     
   13 root      rt   0       0      0      0 S   0.0  0.0   0:00.21 migration/0 
   14 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/0  
   15 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1  
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.14 migration/1 
   17 root      20   0       0      0      0 S   0.0  0.0   0:00.03 ksoftirqd/1 
   19 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+ 
   20 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper     
   21 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs   
   22 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns       
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd  
   24 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback  

```

---

### Post by Doug S on 2014-11-19
> **typos1 said:**
> When you mean sort by "RES" do just mean look at that column ?The default sort order is the %CPU column. By typing the "<" key three times the sort order becomes the RES column. That is what I meant.> **typos1 said:**
> Its hard to read as the output in the terminal changes very second or so, but I ve managed to capture 2 outputsThe default sample interval is 3 seconds. Yes, it can be hard to cut a screen full before it overwrites. However, just set a longer interval time. Example (20 second sampling interval):```
top -d 20
```or run top once in batch mode redirecting the output to a file. Example (I didn't figure out yet how to sort by RES this way):```
top -n 1 -b > top-output.txt
```By the way, I did a batch mode output yesterday and put the result into a spreadsheet and summed the "RES" column. It did NOT add up to what I expected from the "free -m" stuff. But, I digress...

---

### Post by typos1 on 2014-11-19
> **Doug S said:**
> The default sort order is the %CPU column. By typing the "<" key three times the sort order becomes the RES column. That is what I meant.The default sample interval is 3 seconds. Yes, it can be hard to cut a screen full before it overwrites. However, just set a longer interval time. Example (20 second sampling interval):```
top -d 20
```or run top once in batch mode redirecting the output to a file. Example (I didn't figure out yet how to sort by RES this way):```
top -n 1 -b > top-output.txt
```By the way, I did a batch mode output yesterday and put the result into a spreadsheet and summed the "RES" column. It did NOT add up to what I expected from the "free -m" stuff. But, I digress...

Thanks for the reply, did the outputs in my previous posts help in establishing the problem ? Or shall I reset the variables you specified and post again ?

---

### Post by Impavidus on 2014-11-19
> **Doug S said:**
> Example (I didn't figure out yet how to sort by RES this way):```
top -n 1 -b > top-output.txt
```By the way, I did a batch mode output yesterday and put the result into a spreadsheet and summed the "RES" column. It did NOT add up to what I expected from the "free -m" stuff. But, I digress...What about reading the manual ;)?```
top -b -n 1 -o RES
```The difference between the sum of resident memory per process and total used memory minus cache comes from the memory shared among different processes.

The list is a bit incomplete. Firefox is responsible for a quarter of your used memory (450kB of almost 2GB used, excluding cache), but there must be some other memory hugs further down the list.

---

### Post by Doug S on 2014-11-19
> **Impavidus said:**
> The difference between the sum of resident memory per process and total used memory minus cache comes from the memory shared among different processes.I still had the spreadsheet from yesterday. If I subtract SUM SHR from SUM RES is comes pretty close to what "free -m" lists. Thanks.> **Impavidus said:**
> The list is a bit incomplete. Firefox is responsible for a quarter of your used memory (450kB of almost 2GB used, excluding cache), but there must be some other memory hugs further down the list.Agreed. typos1, you will have to re-do it to find the high memory users.

---

### Post by typos1 on 2014-11-19
> **Doug S said:**
> I still had the spreadsheet from yesterday. If I subtract SUM SHR from SUM RES is comes pretty close to what "free -m" lists. Thanks.Agreed. typos1, you will have to re-do it to find the high memory users.

OK, but I thought that it was listing the apps in order of mem use.

---

### Post by Doug S on 2014-11-19
> **typos1 said:**
> OK, but I thought that it was listing the apps in order of mem use.No, because I didn't know how to sort in batch mode, but I didn't care because batch mode is not limited by screen size and lists everything (which, is why I didn't bother to figure it out, but Impavidus showed us how anyhow). My intent with the spreadsheet was to sum everything, just as a sanity check.

---

### Post by typos1 on 2014-11-19
> **Doug S said:**
> No, because I didn't know how to sort in batch mode, but I didn't care because batch mode is not limited by screen size and lists everything (which, is why I didn't bother to figure it out, but Impavidus showed us how anyhow). My intent with the spreadsheet was to sum everything, just as a sanity check.

I tried coding "top -d10" but after that only about 30 applications appeared, there where about 100 when I scrolled down before, so I gave up with it and here are the outputs from system monitor instead:

---

### Post by Doug S on 2014-11-26
> **typos1 said:**
> I tried coding "top -d10" but after that only about 30 applications appeared, there where about 100 when I scrolled down before, so I gave up with it and here are the outputs from system monitor instead:The total number of process lines should equal the number tasks from the second line, I have checked this several times on my systems.
Your posted examples seem to have lots of stuff open, myself I would like to see output from a fresh boot before anything else has been opened or run or whatever. I would like to the file top_3.txt (or whatever you want to call it) after this:```
top -b -n 1 -o RES >top_3.txt
```

---

### Post by typos1 on 2015-02-07
I ve just put up with the problem for the last few months, trying to sort it again now. 

I think I ve found the problem - the system monitor applet is reporting memory usage approx 30% higher than is actually reported in system monitor itself, in my first few posts I said it was the same, I think I must have made a mistake there, because system monitor is showing 50% for "memory" and "swap" is shown as 0, yet the applet says memory load is 80%. 

I ve installed another applet, one that gives a graph output (I prefer numbers) and it shows memory usage at approx 50% but shows cache at about 30% if I click on it and call up its menu. 

So I think sysmonitor applet is including cache as well and looking again at the output of free-m this seems to make sense :

```

~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3952       3664        288        188        141       1538
-/+ buffers/cache:       1983       1968
Swap:          988          0        988

```

taking the "free" and "cached" figures from the "total" figure leaves 2126, which is just over 50% memory usage. Its only done this since 14.10, it has not done it on any previous  version, or at least the figure was not so high on any previous version  of Ubuntu, so I guess that either the way 14.10 reports memory or the  way sysmonitor applet collates its data has changed.

Does my reasoning make sense ? Re-reading this thread, I think Impavidus effectively had the answer all along in these posts :

> **Impavidus said:**
> It seems you changed the swappiness from 60 to  30. That can change the amount of swap used, but shouldn't really  influence the memory usage. It just waits longer before swapping and  then swaps more at once.

The fan usually indicates the cpu is working hard, which also slows  things down. Firefox can use a lot of cpu time if it's playing flash  content. It's not directly connected to memory. You used 50% of memory  there, with another 37% used for cache and buffers. You did not use  swap. What did the applet say there?

You can use [noparse]```
code tags
```[/noparse] to get things in a  box, like for comparison my memory usage:```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          7918       1787       6130         63        101       1017
-/+ buffers/cache:        668       7250
Swap:         8667          0       8667
```Note that I'm on Xubuntu, which uses less memory than Ubuntu.

> **Impavidus said:**
> If the applet said you were using 87% of your  memory, it included the cache. Any properly caching operating system  will use all available memory for cache, so memory usage including cache  will always rise to 100%. As cache is dropped as soon as an application  needs the memory, you can ignore it. So, you were only using 50% of  memory and the applet (and system monitor) don't do a very good job.

The system shouldn't slow down significantly because of high memory  usage until you start using swap. You didn't use swap when you ran **free**.  If your system is slow and not using swap (you should notice the hard  drive activity), check for processes using too much cpu time.

So, problem sorted ! 

. . . or maybe not - when I have nothing running and the system has finished booting, memory usage (not including cache) is approx 30% should it be so high ?

> **Doug S said:**
> The total number of process lines should equal  the number tasks from the second line, I have checked this several times  on my systems.
Your posted examples seem to have lots of stuff open, myself I would  like to see output from a fresh boot before anything else has been  opened or run or whatever. I would like to the file top_3.txt (or  whatever you want to call it) after this:```
top -b -n 1 -o RES  >top_3.txt
```

So I tried to sort htop by res but pressing "<" htop syas "erro try h for help", which I did, cant find any way of sorting by res though.

---

### Post by ancaleth on 2015-02-18
I am experiencing very high CPU usage since moving to Evolution. So I know that is the culprit and the obvious answer would be to find a different Email client, but I specifically wanted a programme syncing Google Calendar, Tasks and Mail. When it runs in the background, it's not too bad, but as soon as I want to do anything within the programme, it munches away the CPU. Combined, evolution and evolution-calendar make up a bulk of CPU usage.

Especially in combination with Firefox open, which is basically always the case. 

Upon running **top** it seems that Firefox is actually using up more of the CPU than Evolution (and this gets even higher when using Google Docs).

Unfortunately I depend on all those Google programmes for work... it's not necessarily my choice. 

Is there anything that can be done to soften the impact on CPU? 

I'm on a Dell Inspiron 64-bit, running Trusty Tahr and this laptop is prone to shutting down if the CPU gets exhausted.



```
top - 12:53:22 up  1:46,  2 users,  load average: 0,34, 0,33, 0,26
Tasks: 201 total,   3 running, 198 sleeping,   0 stopped,   0 zombie
%Cpu(s): 15,8 us, 10,5 sy,  0,0 ni, 73,7 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:   3907692 total,  3335664 used,   572028 free,   216820 buffers
KiB Swap:  4050940 total,        0 used,  4050940 free.  1497256 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                    
 9025 ancaleth  20   0 2048960 746072  66052 S  20,1 19,1   8:45.88 firefox                    
 3058 ancaleth  20   0 1719256 197808  43112 R  40,2  5,1   2:30.40 compiz                     
 8330 ancaleth  20   0 4245012 136200  49872 S   0,0  3,5   0:24.95 evolution                  
 3237 ancaleth  20   0 2826448 101888  29580 S   0,0  2,6   0:09.32 dropbox                    
 3173 ancaleth  20   0 1391748  55448  10892 S   0,0  1,4   0:00.74 evolution-calen            
 3157 ancaleth  20   0 1549900  52548  26572 S   0,0  1,3   0:11.47 nautilus                   
 1846 root      20   0  267068  45360  18904 S  20,1  1,2   3:14.91 Xorg                       
 4221 ancaleth  20   0  769472  29004  18860 S   0,0  0,7   0:00.23 evolution-alarm            
14577 ancaleth  20   0  670756  28548  10524 S   0,0  0,7   0:00.69 unity-scope-loa            
 2852 ancaleth  20   0  684100  27112  17136 S   0,0  0,7   0:04.44 hud-service                
 2872 ancaleth  20   0  646324  26696  12488 S   0,0  0,7   0:39.06 unity-panel-ser            
 2846 ancaleth  20   0  744304  21588  12348 S   0,0  0,6   0:00.58 unity-settings-            
 9011 ancaleth  20   0  724388  20792  13508 R  20,1  0,5   0:01.24 gnome-terminal             
 3177 ancaleth  20   0  730064  18920  13156 S   0,0  0,5   0:02.08 nm-applet                  
 3012 ancaleth  20   0  549472  17768  10884 S   0,0  0,5   0:02.33 ibus-ui-gtk3               
 3139 ancaleth  20   0  492708  17060  12156 S   0,0  0,4   0:00.47 notify-osd                 
 3008 ancaleth  20   0  623048  15944   8252 S   0,0  0,4   0:02.21 bamfdaemon                 
 3073 ancaleth  20   0  656772  15168   8168 S   0,0  0,4   0:00.16 indicator-keybo            
 4641 ancaleth  20   0  501720  14336  10360 S   0,0  0,4   0:00.25 update-notifier            
 3083 ancaleth  20   0 1232984  14120   6928 S   0,0  0,4   0:00.43 indicator-datet            
 3114 ancaleth  20   0 1107992  12444   8752 S   0,0  0,3   0:00.47 evolution-sourc            
 3761 ancaleth  20   0  458404  12216   8896 S   0,0  0,3   0:00.07 telepathy-indic            
 3156 ancaleth  20   0  406600  11964   6936 S   0,0  0,3   0:00.07 unity-fallback-            
14566 ancaleth  20   0  652300  11856   7892 S   0,0  0,3   0:00.29 unity-scope-hom            
 3176 ancaleth  20   0  416172  11840   8384 S   0,0  0,3   0:58.71 indicator-multi            
 2856 ancaleth  20   0  652644  11712   8004 S   0,0  0,3   0:00.24 gnome-session              
 3086 ancaleth  20   0  449860  11708   8144 S   0,0  0,3   0:00.08 indicator-print            
 3806 ancaleth  20   0  550796  10780   5568 S   0,0  0,3   0:00.66 zeitgeist-datah            
14579 ancaleth  20   0  531500  10224   6448 S   0,0  0,3   0:00.05 unity-files-dae            
 1175 root      35  15   23948  10080    928 S   0,0  0,3   0:11.35 preload                    
 3155 ancaleth  20   0  335008   9724   6776 S   0,0  0,2   0:00.06 polkit-gnome-au            
 3162 ancaleth  20   0  134728   8808   2344 S   0,0  0,2   0:00.63 gvfsd-metadata             

```

---

