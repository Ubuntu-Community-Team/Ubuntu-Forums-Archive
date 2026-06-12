---
title: "&quot;Terminal&quot; visible under desktop"
date: 2012-11-24
forum: General Help
---

### Post by frohfroh on 2012-11-24
When upgrading to 12.10, my notebook that has two graphics cards refused to work. I then followed every and each thread on the internet with suggestions and it finally worked. I have naturally no idea of what I did.
But a very annoying thing started happening once every few times I boot: the "teminal"(for lack of better word) is visible under the desktop.
By terminal I mean a black screen with a cursor blinking and a line saying checking battery state. Of course, as it is under my normal desktop, I don't see these things except the blinking cursor that appears in the corner of the screen inside a small black rectangle.
However, every time the screen turns off and on again , I see this terminal, and as I move the mouse cursor the desktop environment is rendered around it.
After further investigation, I found many other weird things going on , including that if I try to use another tty(Ctrl+Alt+ small number), my desktop is slowly rendered over the tty.
If someone has any idea of how to fix it that does not include "just reinstall Ubuntu" I would be very grateful to hear it.

---

### Post by multimiffo on 2013-04-01
> **frohfroh said:**
> When upgrading to 12.10, my notebook that has two graphics cards refused to work. I then followed every and each thread on the internet with suggestions and it finally worked. I have naturally no idea of what I did.
But a very annoying thing started happening once every few times I boot: the "teminal"(for lack of better word) is visible under the desktop.
By terminal I mean a black screen with a cursor blinking and a line saying checking battery state. Of course, as it is under my normal desktop, I don't see these things except the blinking cursor that appears in the corner of the screen inside a small black rectangle.
However, every time the screen turns off and on again , I see this terminal, and as I move the mouse cursor the desktop environment is rendered around it.
After further investigation, I found many other weird things going on , including that if I try to use another tty(Ctrl+Alt+ small number), my desktop is slowly rendered over the tty.
If someone has any idea of how to fix it that does not include "just reinstall Ubuntu" I would be very grateful to hear it.

I see this as well on Xubuntu 12.10 with intel i7 built in graphics and a radeon 7870. Exactly as described above, terminal cursor visible rendering over the desktop and if switching to different tty the desktop renders over the terminal when the draw buffer is updated. Have not found any workaround yet, will try to disable one graphics adapter and see if that helps. Any advice appreciated.

---

