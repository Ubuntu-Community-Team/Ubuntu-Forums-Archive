---
title: "Help me, please?"
date: 2007-10-20
forum: General Help
---

### Post by constchar* on 2007-10-20
I've got some problems that need solving in Gutsy.

First off, the Ubuntu splash screen while Ubuntu is booting causes my monitor to go into a
"Screen Resolution Out of Range" error message.
In fact, I had to do somewhat fancy tweaking to get Ubuntu to even install because the LiveCD would
either crash my computer and the graphics would mess up or I'd get that resolution message so I had to
go into a terminal (Ctrl+Alt+F1) and reconfigure the X-Server to work on my PC followed by a Ctrl+Alt+Backspace.

Second, I have no sound at all.
Once in awhile it seems to randomly work but most of the time I get no sound at all.
I have two soundcards, a Creative Audigy and a RealTek onboard soundcard, I'm using the RealTek at the
moment.

Third, no programs recongize that I have OpenGL but glxgears works perfectly.
kInfoCenter does not display a OpenGL panel and Wine complains about not being able to run DirectX 9
due to no OpenGL and then crashes.
I'm using the nvidia-glx-new package with a EVGA Nvidia 7800 GT PCI Express card.

Thanks for any help!

---

### Post by Akillese on 2007-10-20
Have u tried * USing the*  **Live CD and reinstalling ubuntu** if not tll me

---

### Post by constchar* on 2007-10-20
This is a fresh install straight from the LiveCD.
I also did a MD5 check against the ISO file before burning in case of corruption, which it wasn't.

---

### Post by constchar* on 2007-10-21
Alright I got the sound problem fixed using the Ubuntu Sound Guide and I don't seem to
have the OpenGL problem anymore with Wine.

I still have the resolution problem with the splash/loading screen though.

---

