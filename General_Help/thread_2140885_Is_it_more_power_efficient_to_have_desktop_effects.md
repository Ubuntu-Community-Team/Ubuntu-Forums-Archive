---
title: "Is it more power efficient to have desktop effects turned off (alt+shift+F11)?"
date: 2013-05-01
forum: General Help
---

### Post by Stonecold1995 on 2013-05-01
Is it?  And how much?

EDIT: I meant alt+shift+F12, typo.

---

### Post by vasa1 on 2013-05-01
> **Stonecold1995 said:**
> Is it?  And how much?

EDIT: I meant alt+shift+F12, typo.

I know you've tagged this **kubuntu** ... 

I would think desktop effects have a cost. Measuring the efficiency gained by switching them off would be the hard part. In the **gtk** world, there's something called **gtkperf** but when I played with it for a while I found that measuring the same thing twice didn't give exactly the same result. So, one would have to run gtkperf several times to make sure any change is real. And each run gets my poor laptop quite hot. So I gave up "measuring" and just reduced effects to the minimum according to my understanding of what is heavy or isn't.

Couple of links:
[http://ubuntuforums.org/showthread.php?t=1366362&highlight=gtkperf](http://ubuntuforums.org/showthread.php?t=1366362&highlight=gtkperf)
[http://askubuntu.com/q/29701/25656](http://askubuntu.com/q/29701/25656)

---

### Post by C0NFU53D2 on 2013-05-01
it probably does make a differance, effects or eyecandy are there just for looks and have no reason to be there performance wise (i like my eyecandy :D).  you could test this by turning on/opening a system monitor to monitor CPU usage and RAM usage before and after disabling the effects.  they would have a bigger impact on your performance if you had little ram and/or a low ghz single or dual core cpu.  if the CPU usage or RAM usage is higher when effects are enabled, that means it ***is*** using more battery power.

---

### Post by Stonecold1995 on 2013-05-01
Bascially what I'm wondering is this (sorry if I'm explaining poorly).

Is Inefficient CPU * low effects + 0 (GPU off) < efficient GPU * high effects + CPU?

Theoretically CPU-only software rendering would take less power because the GPU is off and effects are minimal, but the CPU is really inefficient...

Would running "time startx" be accurate or are there to many variables in there to consider?

---

### Post by C0NFU53D2 on 2013-05-01
well, using your processor more will drain your battery just as well as your gfx, although maybe less battery, the less CPU, RAM, Screen Brightness, and GFX you use the longer your battery will last.
which is why suspend lasts so long, all really does is keep your ram so that your cpu, screen brightness, and gfx are not in use, your computer is stil kinda on, but most everything is turned off so it lasts a lot longer.

by "efficientcy" i assume you mean speed, the speed of the cpu will not affect how much battery your effects will use.  but rather the effects them self.

---

