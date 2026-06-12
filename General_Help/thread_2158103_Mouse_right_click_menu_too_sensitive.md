---
title: "Mouse right click menu too sensitive"
date: 2013-06-27
forum: General Help
---

### Post by Bladeforce on 2013-06-27
Hi.

My mouse right click button is way too sensitive. Sometimes it opens and closes so fast i can hardly see it other times it opens so fast and registers a click (generally an open click) with me even seeing anything!! I have set the double click speed in the mouse options to the least it will go but this is more to do with the right click. Double left clicking is fine.
I have run the xev command and this is the output

KeymapNotify event, serial 41, synthetic NO, window 0x0,
    keys:  4294967212 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 41, synthetic NO, window 0x4c00001,
     root 0x2ac, subw 0x4c00002, time 13223160, (36,40), root:(587,475),
    state 0x410, button 3, same_screen YES

If anybody can see an anomaly there please tell me how to sort this out

Ubuntu 13.04

---

### Post by Impavidus on 2013-06-28
It could be a hardware problem, with the right mouse button making bad (intermittent) electrical contact, especially as the left button works fine. Have you tried a different mouse?

---

### Post by Bladeforce on 2013-06-28
I haven't actually will give it a go :)

---

### Post by xl_cheese on 2014-01-06
I've had the same problem on the last couple of Ubuntu releases.  Did you ever find a solution?

---

