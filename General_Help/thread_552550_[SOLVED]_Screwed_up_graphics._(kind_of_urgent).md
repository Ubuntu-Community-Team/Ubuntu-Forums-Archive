---
title: "[SOLVED] Screwed up graphics. (kind of urgent)"
date: 2007-09-16
forum: General Help
---

### Post by Rozenrot on 2007-09-16
Okay, so I just installed the newest ATi drivers for the x800, yay!  Everything worked great until I tried to get my dual monitor set up to work.   After I did what the tutorial said to do, it locked up my computer and thrust me back to the log in screen, with dual monitors enabled, but the problem is is that the frame rate is too much for the second moniter, and that my graphics are totally screwed up on the one that does work.  I can log in but then my screen just sort of...looks ****** up.  I can't do anything, I can't click on any buttons (or where I know there are buttons)

Right now I'm on my mom's computer.

Uhm, is there a way to send ubuntu back in time so to speak?  I know windows has such a thing, but I'm a noob at this.  Help please D:

---

### Post by FRuMMaGe on 2007-09-16
I think it is almost certainly a driver problem with the ATI video.

What you should do is boot into recovery mode (just under your kernel on the boot manager).

No type in "sudo dpkg-reconfigure xorg.conf" without the quotes.

Now simply change the video driver to a default one such as "vesa"

---

### Post by maybeway36 on 2007-09-16
Ctrl+Alt+F1 takes you to a terminal. I suppose you could try
```
sudo dpkg-reconfigure xserver-xorg
```
I just press enter thru everything except what I need to change. Try "vesa" if the ATI drivers don't work.

---

### Post by -=Ghostlike=- on 2007-09-16
You installed 8.41? If you checked Phoronix<->ATi site: 8.41 is only for HD 2xxx version cards, it should be buggy on your card. The driver for pre-2xxx series will come around 12th of october with AIGLX finally enabled for all cards. All dual-screen functions should work then too.

---

