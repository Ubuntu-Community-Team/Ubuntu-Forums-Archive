---
title: "Totem (xine or gstreamer) crash on resize"
date: 2008-05-26
forum: General Help
---

### Post by mattvct on 2008-05-26
II am using Hardy on a Toshiba M200 w/ integrated nVidia GeForce FX Go5200.  Every time I resize or maximize the window when playing back a video the application crashes without an error message.  I've had a similar problem with Firefox 3 Beta 5 where after a certain number of windows they all start coming up black.  I'm assuming that the problem that I'm having is with the nvidia-glx-new driver.  I used VLC to see if it is just a codec problem but VLC won't even open the file.  I've used Totem with both xine and gstreamer back-ends without change (This all worked fine in Gutsy).  Does anyone have any suggestions on anything else I can try?

---

### Post by danzzz on 2008-07-15
I get the same here with nvidia 6600 card. MPlayer also crashed on this same issue. Its a fresh install of Hardy therefore, last "stable" nvidia driver I guess...

---

### Post by danzzz on 2008-07-20
last nvidia-glx updates solved problem

---

