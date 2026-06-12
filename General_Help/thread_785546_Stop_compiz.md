---
title: "Stop compiz"
date: 2008-05-07
forum: General Help
---

### Post by DexterLB on 2008-05-07
I want to stop compiz because my computer is old and it slows it down a lot.

My videocard is old: NVidia GeForce4 MX440 with AGP8x/AGP/SSE2.

So, when I use nvidia-glx, with visual effects enabled everything works fine. BUT when I disable the visual effects, I can't play movies - I start the movie, it works and after ~3min it the player window turns into mess (on totem, vlc, mplayer, haven't tested other). I think the problem is in the nvidia-glx. But if I put nvidia-glx-legacy, the max resolution is 800X600, and I want 1280X1024. Any suggestions? :confused:

---

### Post by Freddy on 2008-05-07
You can stop the windowmanager Compiz-Fusion with 'metacity --replace' without ''. Now you will use the windowmanager Metacity instead of C-F.

---

### Post by DexterLB on 2008-05-07
It works, but again I can't play movies like I explained.

P.S. Why in nvidia-glx-legacy the biggest resolution is 800x600?

---

### Post by Glaxed on 2008-05-08
When you log in, is Compiz started?
If so (or if it is running anyway) try doing the more extreme;
```
killall -9 compiz.real && metacity --replace
```

PS: Are you saying that your videos are fine with the legacy drivers? In that case, then I guess it is driver trouble.

---

### Post by 22flames on 2008-05-08
just go to 

1.System

2. Snaptic package manager ..i know i speeled that wrong lols

4. Go to serch and type in compiz

5.Click and unistalle than it will be gone these should solve your problem

---

### Post by 22flames on 2008-05-08
btw the low res shouldent be a problem with the legacy i had the 400 series agp on my cpu but my res was 1200-1024 so i dont know if thats right :)

---

### Post by sartic on 2008-05-09
> **Freddy said:**
> You can stop the windowmanager Compiz-Fusion with 'metacity --replace' without ''. Now you will use the windowmanager Metacity instead of C-F.

What does it mean? That we can have effects widthout compiz (gives me hard freeze on my intel vga)

---

