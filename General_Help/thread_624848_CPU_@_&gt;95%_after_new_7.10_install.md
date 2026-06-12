---
title: "CPU @ &gt;95% after new 7.10 install"
date: 2007-11-27
forum: General Help
---

### Post by TMarvelous on 2007-11-27
Hi all -

I took my first step into the Linux world yesterday, installing Ubuntu 7.10 on an old laptop.  Installation went fine but after about 20 minutes it would crash.  First time it happened while I was copying files from a networked PC.  Second time I was downloading and installing updates.  I have done a couple of reinstalls and have had same problem every time.

The crash is instant so I feared overheated CPU and what I found is after a clean install when I reboot into Ubuntu my CPU is hovering between 95-100% with no apps running.  The graph shows the high CPU but nothing in the list of processes adds up to 10%.  Makes no sense.

I've searched the forums and couldn't find a similar post.  I'd appreciate any thoughts or suggestions.

My hardware is as follows:
Dell Inspiron 4100
P3 1GHz
~700MB Ram
40GB HD Partitioned in this order:
8.5GB at Root for OS
1.5GM Swap
30 GB /home

---

### Post by eldragon on 2007-11-27
some extra information should be more helpful...

open a terminal (alt-f2, and type gnome-terminal) and run top

see what process is taking up the cpu....

---

### Post by TMarvelous on 2007-11-27
I figured - but didn't know where to get it.  I'm at work now - will post my update in a few hours when I've gotten back home.  Thanks!

---

### Post by daveisadork on 2007-11-27
> **TMarvelous said:**
> I figured - but didn't know where to get it.  I'm at work now - will post my update in a few hours when I've gotten back home.  Thanks!

I was having a similar problem and it turned out to be [Tracker](http://www.gnome.org/projects/tracker), which is turned on by default. There is a bug filed, it's [#153319](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/153319). for the time being you can just execute ```
killall trackerd 
``` in a terminal after you log in and that should keep you from overheating.

---

### Post by TMarvelous on 2007-11-27
I think that was it Dave, thanks!

I had SysMonitor up while I dug up this thread and the CPU had a pretty consistent wave pattern going and as soon as I killed the tracker it flatlined below 10%.

Thanks for the help.

---

### Post by TMarvelous on 2007-11-27
I spoke to soon.  I went back and my CPU is in the 90s again.

Ran TOP:

Scrollkeeper -up is using 85-95% of my CPU at all times.

Please advise.

---

