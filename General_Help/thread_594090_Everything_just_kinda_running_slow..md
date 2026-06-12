---
title: "Everything just kinda running slow."
date: 2007-10-27
forum: General Help
---

### Post by manaleak34 on 2007-10-27
Hey guys for whatever reason everything is kinda running slow on the computer. It worked just fine when first installed but after getting Compiz and messing around a bunch with all the fancy effects and everything else, things just seems to move real slow(take a while for windows to come up, dragging windows is all laggy and creates random lines on the screen, programs like firefox are running slowly) this didn't happen as soon as I turned on the visual stuff (3D box and such) and I've reset the visual effects to normal and still have problems.

Any ideas?

My computer is an Intel Pentium 4 CPU 3.00GHz and has 512MB of RAM with an ATI Radeon 9200 graphics card running Ubuntu 7.10 if you need to know.

---

### Post by whit on 2007-10-27
Have you tried running "top" to see what's using up the resources? Often that's because something has run away a bit. Firefox for instance tends to do that every few days on me.

---

### Post by manaleak34 on 2007-10-27
top - 14:57:20 up  1:11,  2 users,  load average: 0.17, 0.44, 0.56
Tasks: 132 total,   1 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.5%us,  1.8%sy,  0.0%ni, 89.4%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st

According to my System Monitor Xgl usually is taking up the most % CPU which can anywhere between 7% to 33%  and it also seems that it's Status randomly goes between 'Running' and 'Sleeping'. Second in CPU use is gnome-system-monitor which usually stays in the low number range. firefox-bin is third with it's cpu use at very low numbers. According to the system monitor firefox is sleeping.

---

