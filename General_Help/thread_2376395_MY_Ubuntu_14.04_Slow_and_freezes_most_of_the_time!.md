---
title: "MY Ubuntu 14.04 Slow and freezes most of the time?!"
date: 2017-11-02
forum: General Help
---

### Post by fairbird on 2017-11-02
Ubuntu 14.04 LTS
memory ram = 4 GiB
prepossess = Intel® Core™ i3-6100 CPU @ 3.70GHz × 4 
Graphics = Intel® HD Graphics 530 (Skylake GT2) 
Os type = 64-bit
Disk = 500 GiB
My ubuntu is up to date ...
.............

Mu problem is my ubuntu almost eat ram and I got it very slow and freezes especially when I run Chrome browser (with flash or java page as like mediafire site if I upload some files) and then just I can turn power off and on to open it again.
Two or three months ago I did not suffer from this problem.

This is free -h after restart pc 
```
             total       used       free     shared    buffers     cached
Mem:          3.7G       1.5G       2.3G       164M        27M       453M
-/+ buffers/cache:       1.0G       2.7G
Swap:           0B         0B         0B
```
and this is after 5 minutes  with open chrome and log to mediafire fite  
```
             total       used       free     shared    buffers     cached
Mem:          3.7G       3.6G       113M       262M        10M       366M
-/+ buffers/cache:       3.3G       490M
Swap:           0B         0B         0B
```
And this is after close chrome
```
             total       used       free     shared    buffers     cached
Mem:          3.7G       3.5G       250M       295M       131M       737M
-/+ buffers/cache:       2.6G       1.1G
Swap:           0B         0B         0B
```

Here also top result 
when with chrome open it 
```
 3161 raed      20   0 1220548  92032  12176 S  18.9  2.3   2:30.86 chrome                                                                               
 2949 raed      20   0 1646804 776540   5948 S   4.3 19.8   2:05.46 chrome                                                                               
 3004 raed      20   0  489692  39508  11232 R   4.3  1.0   1:02.90 chrome                                                                               
 1773 raed      20   0 1528840  76708  21468 S   2.3  2.0   1:16.01 compiz                                                                               
 1179 root      20   0  478652  94460  83672 S   1.7  2.4   1:05.48 Xorg                                                                                 
 2916 raed      20   0  668460  18904   7600 S   0.7  0.5   0:02.31 gnome-terminal                                                                       
 1522 raed      20   0  376756   1852      0 S   0.3  0.0   0:02.41 ibus-daemon                                                                          
 2651 root      20   0       0      0      0 S   0.3  0.0   0:00.42 kworker/3:0                                                                          
 2866 root      20   0       0      0      0 S   0.3  0.0   0:00.48 kworker/u8:1                                                                         
 3560 raed      20   0   29180   3112   2520 R   0.3  0.1   0:00.06
```
after close chrome
```
                                                                             
 1179 root      20   0  473216 110848  99696 S   2.7  2.8   1:45.43 Xorg                                                                                 
 4148 raed      20   0  668472  30852  23656 S   1.0  0.8   0:01.00 gnome-terminal                                                                       
 1615 raed      20   0  124928    612      0 S   0.7  0.0   0:00.56 at-spi2-registr                                                                      
 1773 raed      20   0 1529196  86808  31200 S   0.7  2.2   1:50.12 compiz                                                                               
 1651 raed      20   0  567376   9352   2880 S   0.3  0.2   0:01.58 bamfdaemon                                                                           
 4186 raed      20   0   29180   3072   2484 R   0.3  0.1   0:00.05 top                                                                                  
    1 root      20   0   33908   1748      0 S   0.0  0.0   0:00.81 init                                                                                 
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                                                                             
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.06 ksoftirqd/0                                                                          
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H 
```

So how can I clean my ubuntu and ram to make it  refresh?!
I Can not install ubuntu again or upgrade it to 16 (Because this version is better for me to my build images and a lot of thing I have on it I can not do it again from beginning)

Also in boot screen how can I remove all old kernel and keep it just newest one ?!

Thank you

---

### Post by Impavidus on 2017-11-02
Chrome can consume a lot of memory, that's by design, but when you close chrome, the memory should be released. I don't use chrome myself though.

Show which processes use most memory, before starting chrome, while running it and after closing chrome.```
top -b -n 1 -o %MEM | head -n 20
```

It seems you don't have any swap, so when you run out of memory the out-of-memory killer becomes active, killing some processes.

As for your other problem, we prefer one problem per thread, so you could start a separate thread about that. But maybe you first want to try autoremove or use the package manager to remove old kernel packages. That should solve it.

---

### Post by mörgæs on 2017-11-02
> **fairbird said:**
> I can not install ubuntu again or upgrade it to 16 (Because this version is better for me to my build images and a lot of thing I have on it I can not do it again from beginning)

You should, nevertheless. 14.04 is dated software and not a suitable choice for a Skylake. Clean install of something new. 

In recent releases you can expect both better performance when running a heavy workload and better power saving when idling.

---

### Post by fairbird on 2017-11-03
> **Impavidus said:**
> Chrome can consume a lot of memory, that's by design, but when you close chrome, the memory should be released. I don't use chrome myself though.

Show which processes use most memory, before starting chrome, while running it and after closing chrome.```
top -b -n 1 -o %MEM | head -n 20
```

It seems you don't have any swap, so when you run out of memory the out-of-memory killer becomes active, killing some processes.

As for your other problem, we prefer one problem per thread, so you could start a separate thread about that. But maybe you first want to try autoremove or use the package manager to remove old kernel packages. That should solve it.
Here result before open chrome
```
top - 14:31:39 up 1 min,  2 users,  load average: 2.88, 0.88, 0.31Tasks: 216 total,   1 running, 215 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.8 us,  1.7 sy,  0.0 ni, 47.5 id, 46.9 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3925164 total,  1082784 used,  2842380 free,   151124 buffers
KiB Swap:        0 total,        0 used,        0 free.   480704 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1894 raed      20   0 1298576  91192  52684 S   0.0  2.3   0:00.96 compiz
 1324 root      20   0  378300  67344  57328 S   0.0  1.7   0:00.89 Xorg
 2016 raed      20   0 1097144  52652  15696 S   0.0  1.3   0:00.06 evolution-calen
 2088 raed      20   0  817300  51432  31108 S   0.0  1.3   0:00.45 gedit
 2166 raed      20   0  858804  44036  37616 S   0.0  1.1   0:00.05 signon-ui
 1954 raed      20   0  876940  42524  30424 S   0.0  1.1   0:00.34 nautilus
 1597 raed      20   0  646392  32844  28024 S   0.0  0.8   0:00.10 hud-service
 2168 raed      20   0  666860  32772  24500 S   0.0  0.8   0:00.14 gnome-terminal
 1948 raed      20   0  692492  32172  24624 S   0.0  0.8   0:00.07 nm-applet
 1593 raed      20   0  823952  30932  22156 S   0.0  0.8   0:00.13 unity-settings-
 1603 raed      20   0  513728  27952  21500 S   0.0  0.7   0:00.17 unity-panel-ser
 1610 raed      20   0  497520  25384  20572 S   0.0  0.6   0:00.09 ibus-ui-gtk3
 1870 raed      20   0  456148  22976  17572 S   0.0  0.6   0:00.03 indicator-print
```

and after open and close it
```
top - 14:40:48 up 10 min,  2 users,  load average: 1.86, 2.41, 1.47Tasks: 213 total,   1 running, 212 sleeping,   0 stopped,   0 zombie
%Cpu(s): 21.4 us,  4.9 sy,  0.1 ni, 55.3 id, 18.3 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem:   3925164 total,  1844680 used,  2080484 free,   228144 buffers
KiB Swap:        0 total,        0 used,        0 free.   738264 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1538 raed      20   0  653752 342180   8492 S   0.0  8.7   1:26.03 gnome-keyring-d
 1894 raed      20   0 1294476  94952  53372 S   0.0  2.4   0:38.42 compiz
 1324 root      20   0  384408  83320  72504 S   6.5  2.1   0:34.48 Xorg
 2016 raed      20   0 1097144  52652  15696 S   0.0  1.3   0:00.06 evolution-calen
 2088 raed      20   0  817300  51708  31112 S   0.0  1.3   0:00.71 gedit
 1954 raed      20   0 1022336  49008  31344 S   0.0  1.2   0:01.20 nautilus
 2067 raed      20   0  159256  35992   5024 S   0.0  0.9   0:30.01 gvfsd-metadata
 1597 raed      20   0  647416  34076  28228 S   0.0  0.9   0:00.49 hud-service
 1593 raed      20   0  825632  32752  22184 S   0.0  0.8   0:00.38 unity-settings-
 2168 raed      20   0  667344  31348  24608 S   6.5  0.8   0:01.40 gnome-terminal
 1948 raed      20   0  692492  30580  25036 S   0.0  0.8   0:00.19 nm-applet
 1603 raed      20   0  514652  29444  21660 S   0.0  0.8   0:00.98 unity-panel-ser
 1912 raed      20   0  440248  27384  22908 S   0.0  0.7   0:00.29 notify-osd
```
Thank you
> **mörgæs said:**
> You should, nevertheless. 14.04 is dated software and not a suitable choice for a Skylake. Clean install of something new. 

In recent releases you can expect both better performance when running a heavy workload and better power saving when idling.
Yes you are right the recent releases more better performance and better power saving when idling ..
But My work can not do it on newest release after 14.04 (I have build dreambox images and I neeed to build old kernel  2.6.18 and old glib 2.19 to those images with 14.04 possible but with 16.04 I can not I got a lot of error compile and build images)

Thank you

---

### Post by Impavidus on 2017-11-03
I didn't know gnome-keyring could consume such an amount of memory, but that still almost 2 GiB free. Can you manage to catch a case where memory is not freed after closing chrome, like you indicated in your first post?

---

### Post by fairbird on 2017-11-04
I found the zeitgeist-fts eat ram when I open chrome and after close it doesn't stop running zeitgeist-fts

---

### Post by Impavidus on 2017-11-04
That seems to be the zeitgeist full text search extension. I don't know the zeitgeist event logger. It's not installed by default on Xubuntu and I wouldn't want it anyway. Maybe somebody knows.

---

### Post by fairbird on 2017-11-04
If I remove it ... Is it causing me problems in the distribution work?!

---

### Post by mörgæs on 2017-11-05
> **fairbird said:**
> 
My work can not do it on newest release after 14.04 (I have build dreambox images and I need to build old kernel  2.6.18 and old glib 2.19 to those images with 14.04 possible but with 16.04 I can not I got a lot of error compile and build images)



Then this is your real problem.
I recommend that you install X/Lubuntu 17.10 in a dual boot and post the build and compile errors you get here in a new thread.

---

### Post by fairbird on 2017-11-05
Can you please more information about ([COLOR=#000000]install X/Lubuntu 17.10 in a dual boot[/COLOR])
How to install another distribute side to side with mu Ubuntu ?!

Thank you

---

