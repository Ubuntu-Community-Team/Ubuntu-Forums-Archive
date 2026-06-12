---
title: "cant change video mode/color depth"
date: 2007-05-19
forum: General Help
---

### Post by geodeath on 2007-05-19
Hello all!
I tried installing latest ubuntu release on my old laptop, with an intel 845 integrated 64mb gfx card.
After a lot of problems (cause the new driver ubuntu comes with does not allow this card to go higher than 640x480) i was able to make it work at 1024x768 by installing the 810 driver.

However, i am stuck at 16bits color. And i know this card can do better.
I tried changing the xorg.conf 100 times, but it wont change the color depth.
I tried changing settings through the xserver-reconfigure but that didnt work either.
No matter if i choose 24bits color at the end of the configuration wizard i am still stuck at 16bits.
any ideas?


George

---

### Post by hamburgerman on 2007-05-19
you might try looking at /var/log/Xorg.0.log and see if you can find any errors relating to your card during x startup. Info there helped me eventually get the nvidia working.

---

### Post by geodeath on 2007-05-19
well, from what i can see from this log is one strange entry:

(==) Depth 24 pixmap format is 32bpp

maybe this is the solution?

However, i am not able to set it up using 32bpp with the xserver-reconfigure tool.

---

