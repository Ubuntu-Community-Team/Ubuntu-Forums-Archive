---
title: "Intel Core 2 Duo running at 1GHz?"
date: 2007-01-09
forum: General Help
---

### Post by HarrisonHopkins on 2007-01-09
In my laptop, I have an Intel Core 2 Duo processor that is advertised that both cores should run at 1.83GHz. However, when I do "cat /proc/cpuinfo" in the terminal, I get a reading that tells me that they are both at only 1000MHz. In Windows, I solved this problem by turning the power saving scheme to Always On. However, I can't seem to find a way to do this in Ubuntu 6.10. Anyone know how I can get all the power out of my processor while plugged into AC, and then minimum while running on battery?

---

### Post by Seq on 2007-01-09
It should be scaling the processor speed, so it will get faster when it is needed. You probably do not want it to run at 100% all the time, even when on AC, as it can cause quite a bit of extra heat (I have a Core Duo 2.0GHz, and it is fanless at 1.0GHz, loud when at 2.0 for any length of time)

---

### Post by HarrisonHopkins on 2007-01-09
Ah, ok. The scaling makes sense, though it would be nice if it was mentioned somewhere in the documentation.

Well, I have another question. I installed Beryl and XGL last night so that I could use Kiba-dock. After installing and logging into XGL and starting Beryl, I hear a strange sound when I scroll any window. What is this?

---

### Post by Seq on 2007-01-09
I'm at home now, so I can give you a little more information.

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

This tells you what governor you are currently using. A quick google search will yeild much better information than I can easily provide, but the end point is that you can tell Linux to use different governors to determine when to clock up, how quickly, and how fast it comes back down.

By default, I think Edgy uses a program called 'powernowd', which handles this stuff in userspace. I can not recall, however..

As for the sound, I get that too. And if I listen carefully on my desktop, it does it as well. I believe it was something to do with capacitors. Don't really know what I can say about that. Maybe somebody else will comment.

---

### Post by HarrisonHopkins on 2007-01-09
My Edgy installation states that it is using ondemand. Is there anyway that I can up the minimum slightly? It wouldn't be much of an increase, Maybe to like 1150 or something like that. 

Wouldn't that eventually damage them severely? The capacitors?

---

### Post by Atomic Dog on 2007-01-10
There is a way to specify the frequency/governors from the cpu scaling monitor.  I don't know the exact way to do it, but if you search the forum you'll find it for sure.  I usually just leave it on on-demand, but sometimes I want it to run full tilt and it's nice to be able to do it.

---

