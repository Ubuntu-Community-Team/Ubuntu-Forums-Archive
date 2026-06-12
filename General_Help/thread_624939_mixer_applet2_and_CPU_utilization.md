---
title: "mixer_applet2 and CPU utilization"
date: 2007-11-27
forum: General Help
---

### Post by richbl on 2007-11-27
Hello all,

I'm running Gutsy (7.10), and using USB audio support for my Plantronics DSP500 headphones.

I've noticed that, periodically, mixer_applet2 begins using excessive and consistent CPU cycles, on the order of 48%-50% (running a duo-core system).

This is significant, and the only way to resolve the problem is to kill and reload the process.

Has anyone else run into similar audio issues with mixer_applet2?

Thanks.

---

### Post by richbl on 2007-11-27
After a little more searching about, it appears that this is a known (Bug #150089 in Ubuntu).

Bummer. Here's to a quick fix!

---

### Post by wolterh on 2008-02-11
It happened the same to me this afternoon. I stopped it and nothing happened. Sound is ok =P

---

### Post by MighMoS on 2008-02-11
My fix for this was just to remove it from my panel (and now I have more space). My laptop has buttons for it, and my desktop has external speakers whose sound I adjust. When I really need to adjust sound like that previously, I just do so through runnning gnome-volume-control manually (or you can unhide its entry in the applications menu by right clicking on Applications and choosing edit menus).

This isn't really a fix, but it works around the problem for me quite well.

---

### Post by zzHanks on 2008-02-27
Same problem here.
I hope this bug will be fixed soon.

---

### Post by ridata on 2008-07-09
Same problem here. Fixed by killing it and it asks to restart, which I say yes to. Sound works fine.

---

