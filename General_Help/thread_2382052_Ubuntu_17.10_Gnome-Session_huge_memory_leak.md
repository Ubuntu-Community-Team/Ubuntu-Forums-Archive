---
title: "Ubuntu 17.10 Gnome-Session huge memory leak"
date: 2018-01-08
forum: General Help
---

### Post by sp40140 on 2018-01-08
I did in-place upgrade from 17.04 to 17.10 (as this worked on my other machine).
17.10 has gnome-session. I am ok with it. 
However, After two days of uptime, gnome session eats up more than 5 gigs out of 8 gigs of ram. And machine basically becomes unusable as I can't launch any new applications. The ones which are already running do work (but a bit slowly).
Also, there are 20 gnome-session processes (ids) in htop window and all show same 5 gigs ram usage.

I did find some bug reports on launch pad from 2014 and few others scattered all over the timeline. However, I don't see any resolution for it.

Any ideas, suggestions? (I might install xfce session and see how it behaves, but I rather fix this if I can).

This happens in both 4.13 (current) and 4.10 (I tried to see if the problem was limited to 4.13 but happens in 4.10 as well) kernels.

Hardware is c2q, 8 gigs of ram. 

Edit: If I log-out and log back in, it frees up the ram. But starts eating up again!

Let me know if you need more information.

PS: Not sure which forum this belongs to, so posted in general help. Kindly move it to proper place if you think otherwise.

Thanks

---

### Post by DuckHook on 2018-01-08
The following will list the first ten processes from *ps* and tell you what is eating up your memory:```
ps aux --sort=-%mem | awk 'NR<=10{print $0}'
```Change the '10' to another number if you want more lines. Post the results back to this thread between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

You should also look at your logs:```
dmesg | tail -n 30
```Again, post results back to this thread.

We need to see what precise processes are eating up your memory to help figure this out.

---

### Post by sp40140 on 2018-01-09
```

dell@DELL:~$ ps aux --sort=-%mem | awk 'NR<=10{print $0}'
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
dell     20368  7.0 27.0 6324628 2189436 tty2  Sl+  Jan08  96:51 /usr/bin/gnome-shell
dell     22276  0.2  6.6 2633688 541432 tty2   Sl+  Jan08   3:00 /usr/lib/firefox/firefox -new-window
dell     25739  0.7  3.8 1486260 311308 tty2   Sl+  Jan08   8:15 /opt/vivaldi/vivaldi-bin 

```

Logs don't have anything unusual.

---

### Post by vasa1 on 2018-01-09
> **sp40140 said:**
> ```

dell@DELL:~$ ps aux --sort=-%mem | awk 'NR<=10{print $0}'
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
dell     20368  7.0 27.0 6324628 2189436 tty2  Sl+  Jan08  96:51 /usr/bin/gnome-shell
dell     22276  0.2  6.6 2633688 541432 tty2   Sl+  Jan08   3:00 /usr/lib/firefox/firefox -new-window
dell     25739  0.7  3.8 1486260 311308 tty2   Sl+  Jan08   8:15 /opt/vivaldi/vivaldi-bin 

```
...
Did you truncate the output?

---

### Post by sp40140 on 2018-01-09
Yes I did. Other processes were from Vivaldi (browser) and update manager. But dropped them as they had HUGE command line.
I didn't think it would be of much help, so dropped it. But I can add it.

---

### Post by mc4man on 2018-01-09
While i see gnome-shell increasing mem use steadily over time it's pretty small here & basically inconsequential. (maybe 3MiB or so an hr. plus  a little out of lockscreen and or suspend 
What you showed in your last post was a bit over 2 GiB, how long did that take to get to?

---

### Post by vasa1 on 2018-01-09
> **sp40140 said:**
> Yes I did. Other processes were from Vivaldi (browser) and update manager. But dropped them as they had HUGE command line.
I didn't think it would be of much help, so dropped it. But I can add it.You can add something like```
cut -c1-100
```to the previous code. I prefer something like
```
top -bn1 -o %MEM | head -20
```or```
top -bn1 -o %CPU | head -20
```

---

### Post by sp40140 on 2018-01-09
It happens because of I log out and log back in. I and keep doing it if push comes to shove. But I use it as part server as well and so it's annoying to having to keep launching the applications.

---

### Post by sp40140 on 2018-01-09
```

dell@DELL:~$ top -bn1 -o %MEM | head -20
top - 21:35:42 up 5 days, 11:34,  2 users,  load average: 1.92, 2.14, 1.59
Tasks: 304 total,   2 running, 302 sleeping,   0 stopped,   0 zombie
%Cpu(s):  5.9 us,  1.2 sy,  0.1 ni, 92.5 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8105440 total,   188684 free,  6092812 used,  1823944 buff/cache
KiB Swap:  2097148 total,  1877384 free,   219764 used.  1334836 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
20368 dell      20   0 7266492 2.985g  84760 S  11.8 38.6 156:40.50 gnome-shell
22276 dell      20   0 2637784 409868  83232 S   0.0  5.1   4:38.10 firefox
21097 dell      20   0 1412044 310448 213224 S   0.0  3.8   8:49.16 vivaldi-bin
25739 dell      20   0 1514024 297860  99784 S   0.0  3.7  17:12.71 vivaldi-bin
20904 dell      20   0 1632524 265876 140020 S   0.0  3.3  36:01.63 vivaldi-bin
22202 dell      20   0 2385372 265204  79172 S   0.0  3.3   2:07.78 thunderbird
21451 dell      20   0 1321520 187644  87120 S   0.0  2.3  16:47.57 vivaldi-bin
21823 dell      20   0 1260208 154480  84788 S   0.0  1.9   3:03.14 vivaldi-bin
21128 dell      20   0 1289628 144056  57844 S   0.0  1.8   0:58.74 vivaldi-bin
20769 dell      20   0 3289516 129852  25404 S   0.0  1.6   1:23.68 dropbox
21153 dell      20   0 1163448 102244  55920 S   0.0  1.3   0:05.59 vivaldi-bin
20396 dell      20   0 1291092 100436  77632 S   0.0  1.2  46:56.53 Xwayland
20731 dell      20   0  880588  98988  26792 S   0.0  1.2   0:04.23 gnome-software



```

---

### Post by vasa1 on 2018-01-09
> **sp40140 said:**
> ...
I did find some bug reports on launch pad from 2014 ...
Here's a more recent one: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1672297](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1672297)

---

### Post by sp40140 on 2018-01-10
Thank you vasa1!
So, is there anything I can do to fix this other than using xfce (or some other session)?

---

### Post by vasa1 on 2018-01-10
> **sp40140 said:**
> Thank you vasa1!
So, is there anything I can do to fix this other than using xfce (or some other session)?

Xfce isn't bad :)

Keep monitoring that bug and hope for a quick resolution!

---

### Post by sp40140 on 2018-01-10
No, xfce isn't bad at all. I have it running on my laptop. :)

I guess I will switch to xfce for now.

PS: Not going to mark this thread "closed" unless mods think it should be.

---

### Post by jbicha on 2018-01-10
What GNOME Shell extensions are you using?

Some extensions have memory leaks.

---

### Post by sp40140 on 2018-01-10
I am not sure. I haven't expressly installed any extensions. I just did in-place upgrade from Unity Ubuntu. So, if the upgrade process installed any by default, only those.

---

### Post by sp40140 on 2018-05-30
So, the memory leak has been identified and fixed in gnome. 
However, the fix is only in version 3.3 so far. And dev are still thinking about back porting the fix to 3.28.
Link : [https://feaneron.com/2018/04/20/the-infamous-gnome-shell-memory-leak/](https://feaneron.com/2018/04/20/the-infamous-gnome-shell-memory-leak/)

The new question:
Can I upgrade gnome version in 18.04 to 3.3 from current 2.28.1 (safely) or does it need extensive testing?

---

