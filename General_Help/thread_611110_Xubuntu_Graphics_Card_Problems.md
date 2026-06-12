---
title: "Xubuntu Graphics Card Problems"
date: 2007-11-12
forum: General Help
---

### Post by wackzingo on 2007-11-12
A few days ago I installed Xubuntu and everything worked fine. I then installed apache2, php and mysql. I restarted the machine and everything still worked fine. I didn't make anymore changes but then I started it up today and it says its running in low graphics mode and couldn't detect the graphics card. Its now defaulting to 800 x 600 and the fonts are extremely small. I restarted a couple times and its still the same. 

I'm currently reinstalling the whole thing, but I am wondering what may have caused this. It's an old 933mhz Dell Optiplex with an integrated graphics card. Is there a way to find out what the integrated card is so I can make sure I have the correct drivers?

---

### Post by PaganHippie on 2007-11-12
> **wackzingo said:**
> I'm currently reinstalling the whole thing, but I am wondering what may have caused this. It's an old 933mhz Dell Optiplex with an integrated graphics card. Is there a way to find out what the integrated card is so I can make sure I have the correct drivers?

You can run *lspci* from a command line and it should list everything on the system bus including your video hardware.  Alternately, you could try looking up the specs for your Optiplex on Dell's website.

Very strange that the video should just wonk out like that.  Let us know if the reinstall fixes the video problem.  It's always possible that the hardware may just be failing.  Then again, I've run into some odd video situations in Xubuntu that were completely fixable by tweaking the settings in *xorg.conf* by hand.

---

### Post by wackzingo on 2007-11-13
Reinstalling seemed to fix it. But I hope it doesn't do it again. I used linux years ago and then tried it about two years ago but wasn't impressed. I'm finally impressed with the possibilities. Maybe I can figure out what caused the problem and will post back here. Thanks for the reply.

---

### Post by PaganHippie on 2007-11-13
I'm never completely ready to rule out gremlins as the cause  ;-)

---

