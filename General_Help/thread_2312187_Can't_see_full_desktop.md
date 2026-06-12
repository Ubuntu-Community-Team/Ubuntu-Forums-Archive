---
title: "Can't see full desktop"
date: 2016-02-02
forum: General Help
---

### Post by dondaniels on 2016-02-02
Installed Ubuntu 15.10 on an XP class HP Dual Core. On boot up, I can see the shut down icon in the top right of the screen. However, when I log in, the right half inch or so of the top menu bar disappears, and I have use Ctl/Alt-Del or Press the power button for several seconds to get the alternate shut down icons. I have tried several monitors and also installed several different video cards, and always the same result. Suspecting it is a software rather than hardware issue. Anyone else have similar issues, or have a fix. If I could shrink the icons across the top of the screen, perhaps the shut-down icon would come back.

---

### Post by howefield on 2016-02-02
Post moved to its own thread and to the "*General Help*" forum.

---

### Post by Vladlenin5000 on 2016-02-02
Hi and welcome.

Are the desktop borders somehow outside the visible area of the TV/Monitor? If not, please give more detailed information; if yes then it's just a matter of adjusting the overscan in your TV. How to do that depends on the manufacturer/model. Please consult your manual and/or post here the exact model and I'll try to do your homework for you :-)

---

### Post by RobertoRecordo on 2016-02-04
Did you run the live DVD before you installed? Was the video working? Perhaps is will help to run the live DVD again and run```
$ sudo lshw -c video
```

The results, if the desktop is rendered properly, will show you the video driver which was used by the live DVD.

I hope this is helpful!

-Rob

---

