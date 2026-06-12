---
title: "General tips to strip down Ubuntu"
date: 2008-06-06
forum: General Help
---

### Post by AndrewTheArt on 2008-06-06
Hey guys,

I'm leaving town for around 6+ weeks and won't be able to physically use my Ubuntu machine during that period of time. I was wondering, what are some general tips to minimize Ubuntu's CPU/Memory utilization during this time period? I want to focus as much of the processor speed as possible on Folding@Home, and not waste it on things that wont be used like nautilus, the GUI, etc...

So what could I safely disable? The GUI is the only thing that comes to mind, and I don't even really know how to do that :)

Thanks,
Andrew

---

### Post by nick_h on 2008-06-07
To stop the GUI:
```
sudo /etc/init.d/gdm stop
```
and to start it again:
```
sudo /etc/init.d/gdm start
```

---

### Post by pointone on 2008-06-07
Your best bet would probably be to switch into runlevel 1 (root prompt); only essential services run at this mode.

---

