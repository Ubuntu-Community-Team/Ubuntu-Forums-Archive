---
title: "memory usage"
date: 2012-11-06
forum: General Help
---

### Post by mcsheffrey on 2012-11-06
Trying to figure out how much memory I'm using, running version 12.04 of ubuntu. When I check "system monitor" it says I'm using .52 Gib, when I check in "top" it shows 1.30 Gib, which is correct, quite a large difference. Any info appreciated.  Roy

---

### Post by papibe on 2012-11-06
Hi mcsheffrey.

Since both 'free -m' and 'top' always been consistent to me, I would go with that.

Just a thought.
Regards.

---

### Post by mardybear on 2012-11-06
Just curious...is preload running?

mardybear

---

### Post by Slim Odds on 2012-11-06
The is THE most asked question in these forums.... by far.

Please read this: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by mcsheffrey on 2012-11-07
What is preload and how do I know if its running.

---

### Post by mardybear on 2012-11-07
These links explain preload a bit:

[http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html](http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html)

[http://askubuntu.com/questions/110335/drawbacks-of-using-preload](http://askubuntu.com/questions/110335/drawbacks-of-using-preload)

As described in the links, there's not really a disadvantage to running preload, it just prefetches data into your RAM so applications open faster but it obviously uses your RAM. Contrary to what some believe, using all or at least most of your RAM is actually a good thing.

If it's running, i believe it shows up as a process when you run 'top' via terminal.

If you're running preload, it's just maximizing your ram. I use preload on my systems and it also appears to give different RAM usage feedback depending on whether i'm monitoring my system via gnome-system-monitor, top or htop.

mardybear

---

### Post by mcsheffrey on 2012-11-07
Tks guys, this explains it. Roy

---

