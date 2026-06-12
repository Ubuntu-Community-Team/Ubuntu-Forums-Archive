---
title: "My 2 Problems"
date: 2008-04-26
forum: General Help
---

### Post by Coto on 2008-04-26
Hey everyone,

I'm having a couple of problems:

1) On startup, the monitor displays a "This Display mode not supported: ...KHz Vertical, ...KHz Horizontal."  

I'm guessing it's a problem with the display mode that's being chosen for the startup process, which file would I find the option to change the horizontal refresh rate?

2) Occasionally when the screensaver activates, it causes the computer to "freeze." Well not really freeze, the screen doesn't return to the login message, instead it remains black, and if you perhaps make a lucky click, you can get the login box to appear to get back to the desktop.

It seems to happen at random, so I'm not sure if anyone has some advice on this.

Thanks in advance,
Coto

---

### Post by pbpersson on 2008-04-26
Both of those problems sound related - as though the video driver is not quite "right" on your system.

You might try searching this forum for articles relating to your specific video card.

To answer your other question, the XServer configuration settings are in the following file:

/etc/X11/xorg.conf

That particular file is so important in the Linux world that you can go to a terminal and type "man xorg.conf" and read about all the different things you can specify in there.

Including mouse settings which I need to work on....now that I happen to be in the file due to your question  :)

---

### Post by Periswell on 2008-04-26
first of all, go into terminal and write

> gksu displayconfig-gtk

this will enter you into screen properties.

secondly, i dont know, just disable screensaver.

hoped it helped 

-josh

---

### Post by Coto on 2008-04-26
Thanks for the help. I'll dive into the video card stuff, and see if I can find it there.  

As for xorg, these settings affect the X11 stuff no?  It seems unlikely that xorg.conf would define the screen refresh rates at bootup, especially since the refresh rates would then carry over to the desktop anyways, in which case I'd have a permanent monitor problem.

However, I'm gonna mess around with different video cards as per the suggestion, I'd rather fix the problem then find a work around.

Thanks for the help both.

---

