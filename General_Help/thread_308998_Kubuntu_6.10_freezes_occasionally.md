---
title: "Kubuntu 6.10 freezes occasionally"
date: 2006-11-29
forum: General Help
---

### Post by Elimist on 2006-11-29
It'll really just freeze whenever. At the log-in screen, when I'm writing a paper, anything. I don't know man.
Mouse doesn't move, if I'm playing any music it starts skipping, and hitting Num Lock or Caps Lock doesn't change their indicator lights.
And I've left my computer just on after that to see if it ever works itself out after a while, and I'll go take care of whatever business. Only a hard poweroff does anything.

I've seen some other people with supposed graphics related freezing, but I don't think that's the case (although I have had problems with my graphics card before).

Hardware stuff:
 - MSI RX480 motherboard
w/ AMD Athlon 64 3200+
 - Nvidia GeForce 7300 GS
 - Maxtor 80gb SATA HD refurbished (I'm wondering if this has anything to do with the various recurring problems I've been having.)
 - anything else, if any one is interested?

It could be a hardware problem, since the hard drive is refurbished, and my Windows XP decided one day that it wouldn't detect any audio devices, even after checking and doublechecking all kinds of things. It's onboard sound, if that means anything. Windows is junk as it is, plus it's not a ligit copy, so this issue probably doesn't mean anything. Oh well.

I've only been on linux for about a month or so, and I've been seeing problems left and right since, despite a lot of help from a room mate who's been running Gentoo and Kubuntu for over a year or so.

---

### Post by akshaysrinivasan on 2006-11-29
Its probably an issue with the graphics card and xserver-xorg ,Try running without open GL.Do you have an onboard graphics card??

---

### Post by Elimist on 2006-11-29
My graphics card is an GeForce 7300, it's a real graphics card.

How would I run without OpenGL? Any suggestions for a way to work around that? Anything I could do in my xorg.conf file or anything?

---

### Post by Elimist on 2006-12-12
Still haven't solved the problem. I hashed out GLX in my xorg, which now appears to be the Open GL thing. Didn't make any difference except some fancy screensavers didn't work very well.

Any help?

---

### Post by Elimist on 2006-12-13
*bump*

I've seen other people with problems like mine on this forum, and I've seen some of them say they've fixed it. So there must be some help out there. Anybody?

---

### Post by henriz on 2006-12-22
I know the feeling. I have experienced the same thing with Ubuntu. So I tried Kubuntu. Same problem. I have found some consistent behavior though: both Ubuntu and Kubuntu only freeze when I use my wireless network. Same as you described: mouse and keyboard do not respond anymore. Screen just freezes as it is.
Using a network cable instead works fine.
A colleague suggested recompiling the kernel, adding only the network components I really have. I have not yet tried this solution.

Hope this helps you and I to tackle the problem.

---

