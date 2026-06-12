---
title: "Memory usage increases without reason"
date: 2020-03-04
forum: General Help
---

### Post by bomberb17 on 2020-03-04
Hello,
I am running Ubuntu 18.04 64-bit desktop on my computer with 8GB RAM.
My system does not run anything special, I only use it for web-browsing (Firefox) and coding using simple text editors.
I also leave my system running 24/7 so I can connect to it remotely using Teamviewer.

There's a very annoying problem though: The memory usage goes up as time passes with no apparent reason. If I don't do a system restart, the memory (RAM + swap) gets filled up 100% and my system becomes unresponsive, and have to do a power cycle.

I cannot pinpoint what's causing this. As I said I'm only using Firefox with about 4-5 tabs open and a text editor. Even if I close all windows, memory usage remains abnormally high (over 60-70% after a few days).

Here are some outputs

```
free -m
              total        used        free      shared  buff/cache   available
Mem:           7841        5710         221        1041        1908         796
Swap:          2047        1559         488
```

and from top:
```
top - 12:32:55 up 4 days, 23:50,  1 user,  load average: 1.24, 1.30, 1.14
Tasks: 320 total,   1 running, 271 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.2 us,  3.5 sy,  0.0 ni, 85.8 id,  0.7 wa,  0.0 hi,  0.7 si,  0.0 st
KiB Mem :  8029380 total,   168672 free,  5790176 used,  2070532 buff/cache
KiB Swap:  2097148 total,   547836 free,  1549312 used.   912620 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                               
29181 root      20   0  190748  19552   7160 S  15.9  0.2 108:08.26 cupsd                                                 
 1856 user  20   0 4021140 219940  44156 S  12.6  2.7  25:14.23 gnome-shell                                           
 1711 user  20   0  888872 211688 174900 S   6.0  2.6  36:43.62 Xorg                                                  
 4599 user  20   0  804796  41032  30184 S   4.3  0.5   0:01.73 gnome-terminal-                                       
 2539 user  20   0 3354920 483840 109272 S   4.0  6.0   1:14.46 Web Content                                           
 1867 user   9 -11 3200700  11880   9544 S   3.6  0.1   0:55.90 pulseaudio                                            
 2071 user  20   0  855028   3272   2176 S   1.7  0.0  68:49.28 conky                                                 
 2324 user  20   0 3940320 432520 162016 S   1.3  5.4   4:43.89 firefox                                               
 4758 user  20   0   47628   4536   3580 R   1.3  0.1   0:03.31 top                                                   
    1 root      20   0  227388   5380   2760 S   0.7  0.1   1:02.29 systemd                                               
 1291 root      20   0  205852 154240   2640 S   0.7  1.9  27:15.91 esets_daemon                                          
 2465 user  20   0 26.618g 190836  94116 S   0.7  2.4   0:32.01 WebExtensions                                         
 3921 user  20   0  985424 213228  91064 S   0.7  2.7   0:44.06 code                                                  
 4687 user  20   0 2760932 198756 133220 S   0.7  2.5   0:07.77 Web Content                                           
   28 root      20   0       0      0      0 S   0.3  0.0   2:48.96 ksoftirqd/3                                           
  531 root      -2   0       0      0      0 S   0.3  0.0   0:14.63 i915/signal:0                                         
 1402 root      20   0       0      0      0 I   0.3  0.0   0:02.76 kworker/u8:3                                          
 1595 gdm       20   0 1098740   8692   4464 S   0.3  0.1   3:22.60 gsd-color                                             
 2014 user  20   0  360696   1584   1128 S   0.3  0.0   0:23.12 gsd-housekeepin                                       
 2922 root      20   0       0      0      0 I   0.3  0.0   0:01.15 kworker/u8:5                                          
 3984 user  20   0  798132 132460  49532 S   0.3  1.6   0:06.61 code                                                  
 4648 root      20   0       0      0      0 I   0.3  0.0   0:00.14 kworker/u8:0                                          
11006 user  20   0 3393200 152388   1688 S   0.3  1.9   6:58.39 Viber                                                 
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.07 kthreadd                                              
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:0H                                          
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_wq                                          
    7 root      20   0       0      0      0 S   0.0  0.0   0:02.76 ksoftirqd/0                                           
    8 root      20   0       0      0      0 I   0.0  0.0  12:29.15 rcu_sched                                             
    9 root      20   0       0      0      0 I   0.0  0.0   0:00.00 rcu_bh                                                
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/0                                           
   11 root      rt   0       0      0      0 S   0.0  0.0   0:01.27 watchdog/0                                            
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0                                               
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1                                               
   14 root      rt   0       0      0      0 S   0.0  0.0   0:01.29 watchdog/1   
```                                         

Can someone help me fix this annoying problem?

---

### Post by GhX6GZMB on 2020-03-04
Firefox. It's notorious for doing this. Update or choose another browser. I've had this on both Win and Lubuntu.

---

### Post by bomberb17 on 2020-03-04
What do you mean update? It's always up to date to the latest version (currently 73.0.1).
How can I verify that this is caused by Firefox and not something else?

P.S. My system froze again and had to power cycle. As I'm writing these lines (only Firefox open with the same tabs as before), RAM usage is at 24% and swap at 0%.

---

### Post by GhX6GZMB on 2020-03-04
Well, if it's updated, Firefox still has the same flaw. Choose another browser. I gave up on Firefox a year ago. It used to be a nice, fast browser, today it's bloatware.

---

### Post by bomberb17 on 2020-03-04
I would prefer for a solution rather than just "nuking" Firefox. I don't want to choose another browser.
After all, I'm still not sure if it is Firefox or something else.
When I leave my system running, I close all windows, including Firefox. Memory still goes up.
Maybe there's a terminal command I can garbage collect the memory?

---

### Post by GhX6GZMB on 2020-03-04
If you close all windows, then why is firefox present in your listing?

---

### Post by jamarsh123 on 2020-03-04
I am managing a small medical office with 4 computers running Ubuntu 18.04. Performance issues (memory) began in late 2019. I've tried everything including trying different operating systems. I too have concluded that Firefox is the culprit. I have installed Brave on all the computers and there are no more problems.

---

### Post by aromo2 on 2020-03-04
> **bomberb17 said:**
> I would prefer for a solution rather than just "nuking" Firefox. I don't want to choose another browser.
After all, I'm still not sure if it is Firefox or something else.

Can you not at least try using a different browser for a couple of days? I suggest Chromium. In a couple of days you'll know if it's the browser or something else. Please let us know the results so you can get further help.

---

### Post by oldfred on 2020-03-04
It probably should not be using cache, but will use all your RAM as cache.

Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
Difference between Details screen on RAM and free command
[http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649](http://askubuntu.com/questions/743649/new-16gb-of-ram-installed-yet-i-see-15-3-on-my-system-why?noredirect=1#comment1106622_743649) &
[https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221](https://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20/184221#184221)

---

### Post by bomberb17 on 2020-03-06
So I think Firefox is indeed the problem: After 2 days of uptime (with firefox windows closed) here are the outputs:

```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7841        2346        1783         775        3711        4425
Swap:          2047           1        2046
$ ps aux |grep firefox
pchatzig  4625  0.0  2.7 3793620 221176 tty2   S+   Mar04   0:00 /usr/lib/firefox/firefox -new-window
pchatzig 13013  0.0  0.0  17700  2256 pts/1    S+   10:50   0:00 grep --color=auto firefox
pchatzig 16856  0.0  3.9 4053708 316632 tty2   S+   Mar05   0:00 /usr/lib/firefox/firefox -new-window
pchatzig 18635  0.0  3.9 4003820 318616 tty2   S+   Mar05   0:00 /usr/lib/firefox/firefox -new-window
pchatzig 32642  0.0  3.8 4173076 307236 tty2   S+   Mar05   0:00 /usr/lib/firefox/firefox -new-window
$ killall -9 firefox
firefox: no process found
$ kill -9 4625
$ kill -9 16856
$ kill -9 18635
$ kill -9 32642
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7841        1387        3114         403        3338        5756
Swap:          2047           1        2046
```


So there were 4 firefox processes eating memory, even with firefox closed. What confuses me is that killall couldn't kill the processes by name and I had to kill them by pid. How can I make a script to run a cronjob?

---

