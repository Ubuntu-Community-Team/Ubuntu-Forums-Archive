---
title: "Dual Monitor Issues"
date: 2007-01-01
forum: General Help
---

### Post by EnterDaMatrix on 2007-01-01
I'm using an ATI Radeon 9500 Pro with the fglrx driver. I have two monitors side by side. One is a Dell Trinitron P780 (Res: 1600x1200 60 hz) and a ViewSonic VPA150 (Res: 1024x768 75hz) Anyway the issue is that I managed to get both monitors working with:

```
aticonfig --initial=dual-head --screen-layout=right
```

Problem is, I have two monitors with two separate desktops, and I can't drag windows between or even use an individual instance of Firefox in both at the same time. Next, I tried using the big desktop option as it said with:

```
aticonfig --dtop=horizontal --overlay-on=1
```

This just send me back to the clone displays where both show the same thing (2 cursors, etc). I've looked around, but I can't find a solution. Basically I would like to have my first monitor (The Dell) be the main desktop, and the 2nd be additional workspace that I can use by dragging windows over and back. I don't want both displays sharing 1 single desktop (Like half of Firefox in one, half in another). I really hope this can be resolved, Windows and OS X have no such problems.

---

### Post by Crooksey on 2007-01-01
Plug both in, then run the commands, however for big desktop to work, both monitors need to be running at the same resolution.

---

### Post by EnterDaMatrix on 2007-01-01
That would explain the problem. So it isn't possible to run big-desktop and run the 2nd monitor as a framebuffer? 1024x768 on both monitors is too small to get any work done. XP had no problem with this. It isn't that I even need big desktop. I just need to be able to run one several windows of the same applications on both screens, dragging isn't so important but it would be nice. Windows just resized them. This isn't possible at all?

---

