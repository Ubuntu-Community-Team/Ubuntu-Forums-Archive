---
title: "animated .gif problem"
date: 2008-05-03
forum: General Help
---

### Post by Ender305 on 2008-05-03
This has been a problem for me since I installed 7.10 and I just decided to wait until 8.04 but it hasn't gotten any better
Animated .gif images won't show up right, they show up as a static image instead of being animated, I'm wondering if I just never had the right packages installed or if its more complicated than that

---

### Post by articpenguin on 2008-05-03
i had this problem when i started to use ubuntu but now i use kde anyways go here.

[http://ubuntuforums.org/showthread.php?t=666158](http://ubuntuforums.org/showthread.php?t=666158)

---

### Post by Ender305 on 2008-05-03
that thread never talks about how to get them to work in firefox, I think they worked for a little while but then I had to reinstall and they stopped again

---

### Post by articpenguin on 2008-05-04
open it with gthumb. I am not sure if gthumb is installed by defualt in hardy.

if its not do 

[PHP]sudo apt-get install gthumb[/PHP]

---

### Post by Ender305 on 2008-05-04
I only care about getting them to work in firefox

---

### Post by clump on 2008-05-31
Most places mention the about:config setting (image.animation_mode).  That didn't help for me.  What did finally get gifs animating in firefox was installing the proprietary nvidia drivers and restarting X.

---

