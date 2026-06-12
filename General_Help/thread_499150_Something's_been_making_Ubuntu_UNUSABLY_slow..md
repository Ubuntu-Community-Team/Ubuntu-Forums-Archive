---
title: "Something's been making Ubuntu UNUSABLY slow."
date: 2007-07-12
forum: General Help
---

### Post by Sweet Spot on 2007-07-12
As of just a few days ago, I noticed that when I open Gaim, all other applications cease to function properly, and take a year and a day to execute. At one point I wasn't even able to click on anything, as resources were totally hog tied. It may be coincidence, but this only started happening after I recently installed Gftp via add/remove. 

The first time it happened was when I was batch uploading a bunch of pictures via Gftp to my atpic.com account, and had opened Gaim. Perhaps it was the other way around though. First thing that happened was that gaim messages were sent through with a large delay, and then at one point the window hung and I had to shut it down, which in its self took forever to do. 

When I go into System Monitor, I do not see any particular instances of multiple running redundant programs, nor do I see any higher than usual cpu or memory spikes for any programs. However, I have a question about the results of : "-m" which is:

>           total       used       free     shared    buffers     cached
Mem:           503        421         82          0         82        211
-/+ buffers/cache:        126        377
Swap:         1026          0       1026


Is that normal ? These results were taken first thing upon booting my machine. Is it normal for so much memory to be used upon start up ? I'm thinking there's a leak somewhere, but don't know if this is true.  I was thinking about just re-installing Ubuntu, or perhaps another distro at this point, but am not sure. It's probably time for a clean up anyway. 

Unless there's a way to totally clean my system without doing such ? Is it possible to wipe out every program (I've installed) and remnant of it having existed, while keeping config files and such in tact as they were when I first installed Ubuntu ? 

I just remembered something else, and noticed something which is making me think that something is corrupted: Yesterday upon boot up, (or the day before) my desktop my usual wallpaper was gone, leaving me with just the plain gradient color I had chosen. And then I noticed when I went to put the wallpaper back, that ALL my wallpapers were gone ? Poof, no paper. I don't get it at all. So I of course put them back which isn't a big deal, but why would this happen ? 

Related, just NOW I noticed that my desktop icons (computer and trash can) are simply not there. I did choose 'default session' when I logged on, but this normally doesn't have such an effect, it never did before ? 

I'm going to back up all my stuff now, and decide what to do. What do you guys make of this, and what do you suggest ?

Doug

---

### Post by Sweet Spot on 2007-07-12
I just hard booted my PC so that my desktop icons would re-appear, and noticed upon shut down " Unmounting local file systems: FAILED"    ?  Re-boot, and it's still the same, no icons. I added my 'computer' icon again, but what the hell is going on here ? I'm definitely going to install a fresh copy of 'something', but I'd first love to know what the hell has happened ? 

Is there some diagnostic tool I can run to see if I borked something ?

Please help me here guys. Thanks. 

Doug

---

### Post by rolfen on 2007-07-12
Try to lauch top from the command line and observe the cpu usage (us = user sy = system ni = nice wa = IO wait and the other i forgot...) should give you a clue of where the problem comes from.
if it's sy it's most probably a prob with the kernel... if it's wa it may be a hardware problem.
Examine the SMART status of your hard drive to see if it's OK.
If it's a problem within the kernel... you can google ktop... but i dont know how useful this would be.

---

### Post by Sweet Spot on 2007-07-12
> **rolfen said:**
> Try to lauch top from the command line and observe the cpu usage (us = user sy = system ni = nice wa = IO wait and the other i forgot...) should give you a clue of where the problem comes from.
if it's sy it's most probably a prob with the kernel... if it's wa it may be a hardware problem.
Examine the SMART status of your hard drive to see if it's OK.
If it's a problem within the kernel... you can google ktop... but i dont know how useful this would be.

Thanks, I'll check. But what of the other issues ? Seems too coincidental that these things should be happening  just because of hogged resources I think. Seems more like a corruption issue IMO.  I'm just not familiar enough with linux/Ubuntu to know where  and how to check. 

Results: > top - 09:42:59 up 48 min,  2 users,  load average: 0.31, 0.24, 0.22
Tasks:  82 total,   1 running,  80 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.3% us,  0.3% sy,  0.0% ni, 99.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    515940k total,   495388k used,    20552k free,    19080k buffers
Swap:  1050800k total,        0k used,  1050800k free,   283104k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5074 masterba  15   0  150m  55m  18m S  0.3 11.1   2:51.69 firefox-bin
 6880 masterba  16   0  2196 1092  856 R  0.3  0.2   0:00.06 top
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.24 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  113 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  115 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  114 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kswapd0
  702 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1832 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1943 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kjournald

Things I noticed: First off, why does it say 2 users. Secondly, what is ni ? It's fluctuating, but when I captured that screen, the usage was 99.3%, and was NOT due to the copy/paste.

---

### Post by rolfen on 2007-07-12
99% id => your CPU is virtually idle!

---

### Post by Sweet Spot on 2007-07-12
Yeah, read that wrong. Thanks for pointing that out to me. So fine, processor is chugging along quite nicely. Memory leak ? Corrupt desktop ? My trash bin is still missing, and I've uninstalled, and then re-installed Gaim, and have totally gotten rid of Gftp as I"m just using Nautilus for my ftp needs now. 

I'll probably still do a clean install of some distro..probably Ubuntu, but thinking about it. Also thinking about whether or not I should do latest-greatest or just stick with Dapper. 

Doug.

---

### Post by qamelian on 2007-07-12
I've been having the same problem with GAIM / Pidgin ever since I did a fresh install of Feisty to compare it with my upgraded install. In my case, top shows GAIM running at 96% or more CPU usage, but this only occurs after someone sends me a message or replies to a message from me. I can send messages all day so long as no one replies. If I get a reply, GAIM goes berserk.

---

