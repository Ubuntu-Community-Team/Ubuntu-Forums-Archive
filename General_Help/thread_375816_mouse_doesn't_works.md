---
title: "mouse doesn't works"
date: 2007-03-04
forum: General Help
---

### Post by dinin_1985 on 2007-03-04
Hello.
I've just finished the dowload of edgy eft and tried my jump to ubuntu but couldn't. Working from the cd my mouse just didn't worked. Since I prefer keyboard accessibility I managed to start the instalation anyway. The problem is that on the screen of time setting (the one with a world map and GMT) it just isn't possible to keep "set time" or "forward" with tab or arrow keys. So I would appreciate if anyone out here could give me a help in putting my mouse to work or instaling the system without it.

---

### Post by DagMan on 2007-03-05
Can you post the output of 
cat /etc/X11/xorg.conf
from the livecd

And also, is it a USB mouse, ps2, a mac mouse etc etc.

---

### Post by dinin_1985 on 2007-03-07
Thanks for the attention. I've already solved the problem: it was all something about editing a xorg.conf  file (it looks like ubuntu is not set to my kind of mouse...).

---

