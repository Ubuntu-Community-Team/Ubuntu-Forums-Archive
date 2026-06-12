---
title: "Another dual core cpu post"
date: 2007-11-19
forum: General Help
---

### Post by pompiuses on 2007-11-19
I'm running Ubuntu 7.10 (Gutsy Gibbon).

I've gotten a new computer at work, and apparently it's running a dual core cpu, At least "cat /proc/cpuinfo" showns two cpus with model name "Intel(R) Pentium(R) 4 CPU 3.00GHz" that runs with 2400Mhz

The problem is that compared some of my work colleges who runs the same setup as me, my computer is very slow.

So I wonder if there are something I need to do or enable, to make dual core cpus work? I've downloaded all the latest updates.

Thanks!

---

### Post by jespdj on 2007-11-19
I'm not sure if that is a dual-core CPU. Maybe it is a Pentium 4 with [hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading) instead of a real dual-code CPU.

Anyway, no, you do not need to do anything special to enable multi-core support on Linux. Do your colleagues really have exactly the same hardware as you?

What exactly is slow? The cause could be almost anything, from wrong graphics drivers to incompatible hardware. Did you see the [sticky post about frequently seen problems with Gutsy](http://ubuntuforums.org/showthread.php?t=595825)?

---

### Post by pompiuses on 2007-11-19
You're indeed right. I compared what my colleagues have in their /proc/cpuinfo, and they've got a different cpu model name.

So it looks like that I've only got a single core hyper-threading cpu as you say :mad:.

---

### Post by atlfalcons866 on 2007-11-19
pentium 4s are not dual core. Pentiums Ds are dual core with just 2 pentium 4s together.

---

