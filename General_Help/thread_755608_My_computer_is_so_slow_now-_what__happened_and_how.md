---
title: "My computer is so slow now- what  happened and how do I fix it?"
date: 2008-04-15
forum: General Help
---

### Post by FoxfirePoet on 2008-04-15
I bought  this computer from my friend, and that started my Ubuntu odyssey. However, when I first got it from her (around 3 weeks ago), it ran very quickly. Now, it has slowed considerably, taking several seconds to open a page or file. Is there anything I can do to speed this thing up again? I looked at the CPU usage and it's not very high, so I don't know what to do. Please help?

---

### Post by yaknowwat on 2008-04-15
Something is probably taking all your memory.

System > Administration > System Monitor

Once Gnome System Monitor is up.
Processes Tab
Then Organize by Memory usage (make sure its "Memory" and not Virtual Memory)
look for anything taking up a lot of RAM space.
Normal users possible suspects are :
Nautilus (memory leaks from media preview caching techniques)
Xgl (incompatible drivers [normally ATI Proprietary ones]  with Xgl causes major memory or CPU usage normally both though)
Wine .exe's that got hung
Loose Stubborn Programs that never closed.

---

### Post by FoxfirePoet on 2008-04-15
Leading Contenders-
Firefox- But it ran quickly before, so I'm confused.
Gaim- also used to run fine
Nautilus-?
wish-?
gnome-system-monitor
gnome-panel -?
gksu
metacity

...which ones should I kill and how do I make them stay dead? Or is that even what I should do?

---

### Post by FoxfirePoet on 2008-04-15
Ending those processes sped it up a  bit but it's still running slow, especially when trying to run videos. Any other advice?

---

### Post by sports fan Matt on 2008-04-15
What are the computer Specs?  Are you dual booting with Windows or did you repartition it to ise Ubuntu only?

---

### Post by FoxfirePoet on 2008-04-15
To my knowledge, it's only running Ubuntu.

Go Sox!

As far as specs go, what do you want to know? It may be a bit before I  can reply- I gotta head to work

---

### Post by FoxfirePoet on 2008-04-15
Still looking for some help here- there must be something I can do to help re-speed this thing.

---

