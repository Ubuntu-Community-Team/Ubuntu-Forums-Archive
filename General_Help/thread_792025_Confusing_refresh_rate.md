---
title: "Confusing refresh rate"
date: 2008-05-12
forum: General Help
---

### Post by sleepingdragon on 2008-05-12
I've got an interesting dilemma. My display preferences are giving me the usual dodgy refresh rates of 50/51/52Hz on my nVidia 6200 card, but my monitor OSD info is showing me a 75Hz refresh rate. Now, I'm quite fussy on flicker, so 50Hz would be noticeable to me. However, the screen is easy on the eyes so I'm going to say that my monitors OSD is correct. Could it just be a bug? 

Since it doesn't seem to be creating any obvious problems I'm not unduly worried, but it might have led some people to try and fix a refresh rate problem when there wasn't one in the first place.

My Xorg is the original xorg/nvidia-glx-new config, no manual changes.

Anyone got a clue on this?

EDIT: installed *nivida-settings*, it also confirms 75Hz refresh rate. I'm seriously guessing this is an Xorg bug.

---

### Post by chewearn on 2008-05-13
It's not a bug.  It a hack by nvidia driver.  It has to do with supporting dynamic twinview feature  by tricking Xorg with false refresh rate info.

[http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/chapter-13.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/chapter-13.html)

Scroll down to the section under "Dynamic Twinview".

.

---

### Post by sleepingdragon on 2008-05-13
Thanks for the link, that certainly makes a lot more sense. Still doesn't help some poor souls who may be looking at their refresh rates and wondering why it isn't right.

As indicated in the link, there may be hope that this will be fixed sometime in the near future.

---

