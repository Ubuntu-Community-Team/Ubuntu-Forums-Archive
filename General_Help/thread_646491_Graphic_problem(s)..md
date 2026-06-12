---
title: "Graphic problem(s)."
date: 2007-12-21
forum: General Help
---

### Post by Trinexx on 2007-12-21
Well, let me begin by giving you the background story. Some time ago I switched from Kubuntu to Ubuntu, and immediately started to hate KDE. Now, I would have been fine with the simple "apt-get install ubuntu-desktop", but that left me with a bunch of kubuntu apps I didn't really appreciate. Given my tendency to experiment as much as humanly possible, I decided to go with a full reformatting, mostly because I wanted to set another hard drive as my home folder. Anyways, the reinstall solved a lot of problems I had been experiencing, due to my noobish nature when I first started using *buntu. However, it left me with one rather unpleasant issue.

Everything media related runs like crap now. Games, movies, and especially FLV players (youtube and the like). I had to jump through all sorts of hoops last time to get OpenGL to run on this computer, but when I finally accomplished the task, it worked fine. On this install it runs out of the box, but runs terribly. By terribly I mean "5 frames per second in Q3 Arena IF I'm lucky".

Now that you know the nature of my complaint, I suppose it's time to start dumping out some specs and conf files.

P3 1ghz processor, 198mb SDRAM, Intel 810e chipset (onboard video, I know). If the rest of the specs would come in handy, let me know. Xorg.conf is attached, but I think I left out another video-related file. If more information is needed, I'd be more than happy to provide.

Even if this problem isn't solved, thanks for taking the time to read this.

---

### Post by approaching on 2007-12-21
i am guessing that you went and got gutsy when you installed ubuntu after all of that business, which happens to have compiz enabled by default. you may want to look into replacing compiz with metacity when you want to play games. it's just metacity --replace, then when you are done it's compiz --replace. your computer isn't fast, it should be just fine for most things besides gaming, but it isn't going to run compiz in the background and the game fluidly at the same time, especially with that little of ram and an on board video card. try testing some things out and see if you are even getting 3d acceleration from your card, you might not be at all. some of those open gl screen savers seem to be a good test to see if everything is working as it should.

---

### Post by geirha on 2007-12-21
An easier way of switching between compiz and metacity is to go to System -> Preferences -> Appearance -> Visual Effects.

---

### Post by Trinexx on 2007-12-21
The first thing I did after reinstalling was remove compiz. I appreciate the help, but I managed to solve the problem myself. Not sure what I did to solve it, but regardless, it's solved o_O

Faced with a new problem now, but I suppose it would be better to start a new thread.

---

