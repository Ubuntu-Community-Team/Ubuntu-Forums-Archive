---
title: "kworker driving me crazy--please help"
date: 2012-12-13
forum: General Help
---

### Post by Dopaque on 2012-12-13
So, I have a recent install of Ubuntu 12.10 on a Samsung Chronos 7.

Every time I run top, a kworker process is eating almost one of my CPUs.

```
jam@jam-flatbox:~$ top

top - 12:32:11 up 10 min,  2 users,  load average: 1.02, 0.98, 0.62
Tasks: 207 total,   2 running, 203 sleeping,   0 stopped,   2 zombie
%Cpu(s):  0.5 us,  9.5 sy,  0.0 ni, 90.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   7897736 total,  1052328 used,  6845408 free,    71048 buffers
KiB Swap:  3906556 total,        0 used,  3906556 free,   534780 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
   67 root      20   0     0    0    0 R  74.2  0.0   8:01.43 kworker/0:2       
 1181 root      20   0 60940  14m 5240 S   5.7  0.2   0:35.65 Xorg              
 2875 jam       20   0  661m 149m  34m S   2.3  1.9   0:50.65 firefox           
 3358 jam       20   0  151m  15m  11m S   1.3  0.2   0:00.32 gnome-terminal    
 1962 jam       20   0 68784  17m  10m S   0.7  0.2   0:02.99 compiz            
   82 root      20   0     0    0    0 S   0.3  0.0   0:00.22 kworker/4:1       
  942 messageb  20   0  4076 1900  912 S   0.3  0.0   0:00.71 dbus-daemon       
 2004 jam       20   0 54748  18m  10m S   0.3  0.2   0:00.31 wicd-client       
 2148 jam       20   0 38796 2596 2176 S   0.3  0.0   0:00.02 gvfs-afc-volume   
    1 root      20   0  3636 2036 1284 S   0.0  0.0   0:00.56 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.01 ksoftirqd/0       
    6 root      rt   0     0    0    0 S   0.0  0.0   0:00.06 migration/0       
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 watchdog/0        
    8 root      rt   0     0    0    0 S   0.0  0.0   0:00.01 migration/1       
    9 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kworker/1:0       
   10 root      20   0     0    0    0 S   0.0  0.0   0:00.02 ksoftirqd/1       

```


This means that the fan is always on and my battery life is dismal.

I have scoured the internet for fixes to this but none of them have worked. editing grub to add "pci=noapci" or "apci=off" doesn't work.  tried to update my kernel but I'm too much of a linux noob to pull it off. I currently have 3.5.0-19-generic and have been unable to update to a different one (even though I tried! I followed several different instructions, one involving a sh script and one involving debs, and nothing happened) 


I'm tired of my fan running constantly and my computer being used like this. Help!

---

### Post by Dopaque on 2012-12-13
all right--I seem to have solved my own problem, with the help of my linux-savvy cousin.

Updated kernel to 3.6.9 and kworker is back to being a silent background process.

YAY SUCCESS

---

### Post by Mopar1973Man on 2012-12-13
Would you mind posting how you did the update?

---

### Post by Dopaque on 2012-12-13
I did it by following the instructions at this site exactly: [http://www.itworld.com/software/326691/upgrade-ubuntu-1210-or-1204-linux-kernel-369](http://www.itworld.com/software/326691/upgrade-ubuntu-1210-or-1204-linux-kernel-369)

I also installed kernel 3.6.3 and tested that, and it worked as well. You can find the deb at: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/)  (use the "image" deb)

extract it into a folder, then cd into that folder and type in the terminal, ```
dpkg -i *.deb
```

that should take care of it too.

---

### Post by nacho2002 on 2012-12-14
Thanks for your help Dopaque! this problem was getting me mad! 
Did you also install something for the keyboard backlight control? i can't get it to work properly!

---

### Post by Dopaque on 2012-12-14
Keyboard backlight control... come to think of it, no, my keyboard backlight doesn't come on anymore that I can tell. But I don't generally look at the keyboard when typing so it hasn't bothered me yet. Im actually kind of glad it doesn't work since it was just using unnecessary power.

sorry idk how to help you!

---

### Post by nacho2002 on 2012-12-14
Ok, no problem! Thanks anyway!
I installed samsung tools, and it turns on, but i can't control the intensity. I also got some scripts to have both mouse buttons in the touchpad! If you need them, let me know and i'll find them again!

---

### Post by Dopaque on 2012-12-15
[COLOR="DarkRed"]so, this kworker problem apparently is not completely solved.[/COLOR]

I was in kernel 3.6.9 today and the fan wouldn't go off... turns out kworker was taking up 70+% of one cpu again.

ARGH.

I restarted and booted into kernel 3.6.3. In my old kernel, kworker was constantly on. It seems that in kernel 3.6.9, kworker generally behaves, but on some boots will go crazy.

Still looking for a permanent fix!! (re-trying acpi=off in grub... gah, we'll see)

---

### Post by babixeddu on 2012-12-28
Hi Dopaque, have you got any news?

take a look also at this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793")

---

### Post by Dopaque on 2012-12-29
changed to 64 bit linux, kernel 3.6.3 ... worked great for a few days, now kworker is going crazy again and continued even after a restart.

I think kworker started going crazy after I suspended my machine by flipping the lid down and then turning it back on. A restart did not help. I am about to shut down and reboot and see what kworker is doing.

---

### Post by Dopaque on 2012-12-30
I can kinda sorta confirm that my kworker problems are caused by laptop suspend.

*sigh* ...I thought I was finished having to disable suspend and hibernate on my laptops since Hardy Heron...

any fixes that mean I can still suspend and hibernate without kworker trying to kill me would be greatly appreciated.

---

### Post by babixeddu on 2013-01-07
Hi,

for a working-workaround, check out:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793")

and follow my instruction at #114 and #117 or the Alex version at #116

:guitar:

---

### Post by Dopaque on 2013-01-13
update:

acpi=off and apci=noapci break a lot of things and are generally obnoxious fixes. acpi=noirq seems to be working okay for me. Since I put it in the kernel line I haven't had problems with kworker, and I can still suspend my laptop by flipping down the lid but I don't think I can make it hibernate.

I still need to mess with some power management stuff in order to get a good battery life, but not having a runaway process taking up 70+% of one core is certainly helping.

---

### Post by samwillc on 2013-01-13
Hi.

Is there some kind of power management issue in ubuntu 12.04 going on?

This is worrying as I was going to buy a laptop and run ubuntu rather than a macbook. But I have seen various posts on forums where people are getting very low battery life out of brand new laptops which should be 6 or even 7 hours.

Please could someone comment on this possible issue if it is one. It is a very important point in my decision on which laptop to buy! Thanks.

Sam.

---

### Post by Dopaque on 2013-02-04
Yes, there are power management issues with at least ubuntu 12.10 (I can't speak for 12.04). I'm kind of casting about for possible fixes atm, but I haven't made major inroads yet.

I think older distros of ubuntu are better at it? People say 12.04 is better than 12.10. And of course there's other linux distros that might work better for you than ubuntu. I would definitely prefer linux over a mac anyday (no DRM, more control over your own setup, etc etc) so I wouldn't give up, but yeah I would steer away from 12.10 for now anyway.

---

