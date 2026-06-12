---
title: "Gui won't boot"
date: 2007-12-27
forum: General Help
---

### Post by Dracar on 2007-12-27
its been awhile since ive got on my ubuntu partition, mainly because i couldn't use WoW and Vent, and those are what ive been on a lot recently, that and i can't seem to change my screen resolution to something i like... Well anyways, i went on today and updated a lot of my files and now when i boot up it sticks at the mouse spinning before it loads the gui, i can still get the black screen with cmd line prompt or w/e up so i am assuming i have to re install the gui, can some one explain this to me?

---

### Post by iris-n on 2007-12-27
It looks like your update has somehow screwed X.

It might be that it's only misconfigured. Try running:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This way it gets the setting again automatically. If you prefer do it manual:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Dracar on 2007-12-27
Meh, I've had enough of working with it manually so il do tha auto, for some reason i don't think it will work, think i tried before... lemme wright down the cmd and try it...


Oh man, now its off again lol, it says failed to start x server, disabled till it is configur3ed properly. so what vid. driver am i suposed to use now? i clicked vesa cause thats what i did last time i had this problem but that was on an older version too. Thanks in advanced.

---

