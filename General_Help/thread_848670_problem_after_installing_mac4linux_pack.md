---
title: "problem after installing mac4linux pack"
date: 2008-07-03
forum: General Help
---

### Post by csc2ya on 2008-07-03
I thought i'd change the theme on my laptop, and came across the mac4linux transformation pack. I've done all the customizations apart from changing the panel icon.

However, i'm unable to put the apple icon in the correct folder as I don't know which folder it needs to go in. I went to check in preferences to find out the name of the theme, but now, whenever I click on the system menu in the panel menu, my cpu usage goes up to 100%, and everything freezes.

When this happens I can only power off by holding the power button, or press ctrl+alt+backspace to restart xserver. Anything else I try doesn't work.

I can't figure out what's causing this. My current memory usage and system loads are as follows if it's likely to help pinpoint what the problem is:

```
administrator@Laptop:~$ cat /proc/meminfo
MemTotal:      2066152 kB
MemFree:       1078244 kB
Buffers:        146960 kB
Cached:         365180 kB
SwapCached:       1516 kB
Active:         546740 kB
Inactive:       264068 kB
HighTotal:     1169984 kB
HighFree:       496460 kB
LowTotal:       896168 kB
LowFree:        581784 kB
SwapTotal:     6048432 kB
SwapFree:      6006168 kB
Dirty:             288 kB
Writeback:           0 kB
AnonPages:      297288 kB
Mapped:          74368 kB
Slab:            35996 kB
SReclaimable:    25616 kB
SUnreclaim:      10380 kB
PageTables:       2956 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   7081508 kB
Committed_AS:  1380880 kB
VmallocTotal:   114680 kB
VmallocUsed:     10180 kB
VmallocChunk:   104052 kB
administrator@Laptop:~$ uptime
 23:00:14 up  1:05,  2 users,  load average: 1.83, 1.30, 1.24
administrator@Laptop:~$ 

```

Has anyone got any idea's on how to fix it?

---

### Post by csc2ya on 2008-07-06
I hate to bump this, but does anyone have any idea's about it? It's starting to get annoying now. I also get exactly the same problem if I login using failsafe gnome.

In addition, when it freezes, the only way to reboot without just powering off is to restart x by pressing ctrl+alt+backspace and then restarting from the login screen.

---

