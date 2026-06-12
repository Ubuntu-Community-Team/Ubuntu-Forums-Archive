---
title: "Help I lost my desktop! (related to NVIDIA drivers)"
date: 2007-09-07
forum: General Help
---

### Post by Jenuall on 2007-09-07
Hi there I'm hoping somebody can help me.

I'm using feisty and tried to enable the desktop effects, which meant enabling the nvidia drivers. This worked okay, but then I found that with the desktop effects enabled I started to run into various graphical defects. So I tried turning off effects and disabled the nvidia drivers and now when I startup I can get through the log in screen but then nothing else displays on the screen, I'm just left with the mouse pointer which I can move around on a plain white background!

Is there a simple solution to get my desktop back?

---

### Post by jim_p on 2007-09-07
If you hit Alt+F2 you will get a "Run command" box
Try running metacity from there
```
 metacity --replace 
```

I dont think that the drivers are related to this because if they had any problem, you woulden't be able to see the logon screen either

---

### Post by Jenuall on 2007-09-07
Well that seems to have done the trick, thanks a alot!

I made the assumption it was driver related as that was the only thing I had done the previous time I had logged on.

Is there any way to make it so that I don't have to do the "metacity --replace" thing each time I log in?

---

