---
title: "Higher and more varying cpu usage in ubuntu than xp."
date: 2007-03-20
forum: General Help
---

### Post by JCasper on 2007-03-20
Yeah, just curious if this was the norm. I am new to ubuntu and noticed in htop that my cpu usage varies more and seems overall higher than in xp. Also, my swap is not getting used, but I guess this is because my memory has plenty of space?

Thanks.

---

### Post by nsleiman on 2007-03-20
Well i just have the opposite here, but as for the swap, i set the swappiness to 20 so my memory is not fully occupied. (laptop) i have 512 only.

---

### Post by JCasper on 2007-03-20
I read that edesklets require a lot of cpu usage. I am guessing that is what is mostly causing the fluxuation.

---

### Post by JCasper on 2007-03-21
Well, I disabled my edesklets and my cpu still seems to be over working itself.I noticed this weird long "thing" that sucks up cpu%, anyone know what this even is?

/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/ :0.Xauth -nolisten tcp vt7

lol....what in gods name is this, and why is it sucking resources?

---

### Post by hikaricore on 2007-03-21
That's your X server.

aka your linux gui from graphical login screen to desktop and everything after.

What kinda video card do you have, and have you installed the right drivers for it?  :)

Check the output of:

```
glxinfo | grep rendering
```

If this returns **No** you may need to look into fixing/setting up drivers.  Example, you have a video card that is not properly setup or doesn't have the best driver installed, this means your cpu is doing all the work your gpu (video card processor) should be doing to draw everything you see from login onward.  Hope this makes some sense.

---

### Post by JCasper on 2007-03-22
That does make sense, I will check that out right now. I was so busy making my desktop look cool I forgot about the important stuff:) Thanks

---

