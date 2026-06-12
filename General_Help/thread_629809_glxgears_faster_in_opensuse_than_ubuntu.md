---
title: "glxgears faster in opensuse than ubuntu"
date: 2007-12-02
forum: General Help
---

### Post by larini on 2007-12-02
Hi, after install both system in the same machine and after install the same nvidia drivers, i'm getting about 5000 fps in ubuntu gutsy and 9000 fps in opensuse 10.3 (kde) using the glxgears.

Is this glxgears a good tool to measure 3d speed?

---

### Post by larini on 2007-12-03
bump!

---

### Post by skymera on 2007-12-03
glx gears in my opinion isnt a good benchmark tool, i dont think its deisgned for it, just to test 3d rendering i elieve.

what is youre graphics card?

---

### Post by anaconda on 2007-12-03
yep.. glxgears isn't a good bencmark tool.

Just look at my glxgears output:
```
6098 frames in 5.0 seconds = 1219.547 FPS
6437 frames in 5.0 seconds = 1287.289 FPS
2382 frames in 5.0 seconds = 476.107 FPS
1152 frames in 5.0 seconds = 230.250 FPS
1137 frames in 5.0 seconds = 227.212 FPS
1136 frames in 5.0 seconds = 227.179 FPS
1146 frames in 5.0 seconds = 229.057 FPS
5824 frames in 5.0 seconds = 1164.794 FPS
2690 frames in 5.0 seconds = 537.892 FPS
2579 frames in 5.0 seconds = 515.798 FPS
2264 frames in 5.0 seconds = 452.550 FPS
9700 frames in 5.0 seconds = 1939.941 FPS
19408 frames in 5.0 seconds = 3881.494 FPS
29590 frames in 5.0 seconds = 5917.891 FPS
29557 frames in 5.0 seconds = 5911.328 FPS
35630 frames in 5.0 seconds = 7125.867 FPS
49069 frames in 5.0 seconds = 9813.602 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

First 2 lines are about normal for my machine, but then I changed the size of the glxgears window, and put it under other windows.. And ofcourse the speed will change depending of other load on your machine..

Glxgears and glxinfo are good tools for checking that your 3d-acceleration works..

---

### Post by mcduck on 2007-12-03
> **larini said:**
> 
Is this glxgears a good tool to measure 3d speed?

No, it's not. That's why it used to be so you had to run glxgears with 'glxgears --iacknowledgetthatthistoolisnotabenchmark' to get the fps readings with it.. :D

---

### Post by larini on 2007-12-03
Ok, guys. My board is a nvidia 7600 gs.
There is a good tool for benchmark?

---

