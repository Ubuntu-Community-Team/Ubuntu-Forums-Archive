---
title: "Fan runs constantly when I boot into Ubuntu"
date: 2007-01-11
forum: General Help
---

### Post by apathos on 2007-01-11
My cpu fan runs constantly when I boot into Ubuntu (EE 6.10).  I have a dual boot, with XP on one HDD, and Ubuntu on another.  In XP, my fan is very quiet, very hard to hear.   In Ubuntu, my fan runs constantly at high speed.  

Is this normal?  Is this acceptable?  Is something heating my CPU up?  Why only in Ubuntu?

---

### Post by bettlebrox on 2007-01-11
What kind of processor do you have? U may need to install the speedstep or cpufreq modules that will allow your processor to change frequency on demand (if it supports it).

On my Pentium-M laptop, I have the speedstep_centrino module loaded, also the cpufreq_* modules loaded.

---

