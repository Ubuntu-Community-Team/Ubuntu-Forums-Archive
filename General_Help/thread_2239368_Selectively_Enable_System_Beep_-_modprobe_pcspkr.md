---
title: "Selectively Enable System Beep - modprobe pcspkr"
date: 2014-08-13
forum: General Help
---

### Post by AmagicalFishy on 2014-08-13
Hey, everyone.

Often I have to wait a few minutes for something to compile. Instead of glancing at the screen every now and again to see if it's finished, I've installed *beep *and enabled the system beep via *modprobe pcspkr. *This way, I can do something like "make; beep"&#8212;and just rely on the system beep to know when something's finished compiling.

The unfortunate aspect of this is that the beep is enabled for everything else, too. For example, if I press delete in an empty Python interpreter, I'll get a beep.

I'd like to disable beeps for everything *but *the beep command. Does anyone know how to do that?

My idea was: Change the beep alias so that it did something like:
modprobe pcspkr *on*
beep
modprobe pcspkr *off*

Though, now that I've enabled the speaker, I don't know how to disable it.

Edit: Found it! modprobe -r pcspkr

Is there a better way to enable this for a single program? Or is the alias thing my best shot?

---

