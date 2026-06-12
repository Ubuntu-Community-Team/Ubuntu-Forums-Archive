---
title: "What does this mean &amp; why is it using 99% of my cpu?"
date: 2007-06-22
forum: General Help
---

### Post by NT4usB on 2007-06-22
My Mythbox is acting up.
(copied from htop)
```
/usr/bin/X :0 -br -audit -auth /var/lib/gdm/ :0.Xauth vt7 -
```
Should this be 97-99%?
If I pause playback, it drops to zero.
Come home lately to find it locked up solid. No remote, keyboard, mouse. Can't ssh into it. 
Paused it this morning for a few minutes, came back to find it locked again.
It ran great for a year, now this.
Only thing I've messed with lately is trying to get vnc and some nfs shares to work...
Any thoughts on where to start chasing the problem?

this is interesting```
mythtv@dapperpvr:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01df (rev a1)
```Maybe the nvidia driver is jacked up?

More output```
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01df (rev a1) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology: Unknown device 340e
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at da000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at db000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at dc000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] #10 [0001]

```

xorg.conf:
[http://home.pacbell.net/clayt/dapper.xorg.txt](http://home.pacbell.net/clayt/dapper.xorg.txt)

---

### Post by NT4usB on 2007-06-23
More info...
I replaced xorg with a backup from before I started messing with nfs, etc. Still locks up.
When it's locked up my Linksys switch activity lights are going nuts. All three (master fe/be, slave fe/be, and router) lights blinking wildly.
Even after I reboot the master, the slave won't connect to Myth. Have to restart it to get it going again.
Maybe coincidence but it seems mythfilldatabase is running when it locks so I'm going to move that out of cron and see if it stops.
If I run mythfil manually, it runs no problem.
Any ideas?

---

### Post by Silenus on 2007-06-23
From what I read it looks like a video card problem. I haven't heard of a problem on dapper like this before though.

---

### Post by NT4usB on 2007-06-24
Moving mythtv-backend out of cron didn't change anything. Locked up again.
Going to reinstall the video and see if that changes anything.
Gotta be a clue in the switch going nuts... Wondering if the nic could be causing it?
Whatever it is, it jacks up both computers...

---

### Post by NT4usB on 2007-06-26
effen pos is pissing me off...
I took the switch out of the equation and went straight to the hub.
Still locks both computers (at least) once a day.
pos ran great for eight months and now it's garbage.
guess I'll go the windows route and reinstall the whole mf thing.

---

