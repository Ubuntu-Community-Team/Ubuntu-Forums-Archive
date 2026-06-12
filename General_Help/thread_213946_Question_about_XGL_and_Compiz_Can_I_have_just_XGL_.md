---
title: "Question about XGL and Compiz: Can I have just XGL without Compiz?"
date: 2006-07-12
forum: General Help
---

### Post by darkpark on 2006-07-12
Could someone clear this up for me please?
Is XGL opengl accelerated Xorg/x-windows and compiz provides the special effects?
Is it possible to have just the opengl acceleration ( for a faster desktop ) but none of the special effects?

---

### Post by o_fortuna on 2006-07-12
You could set up your desktop to use XGl, but without an accelerated window manager (ie compiz), you would see none of the effects -- including the increased desktop speediness.

The reason is that Metacity (the default window manager) does not use graphics acceleration in any of its funtions. You would need compiz to notice any speed differences.

That said, you could install compiz and disable most of the effects. I personally loathe 'wobbly' and several other effects, but I enjoy the increased snappiness and the zoom funciton.

---

### Post by RAOF on 2006-07-12
Actually, there is a reason you might want to use XGL without compiz: if you've got an ATI card, and want to have both OpenGL acceleration **and** the composite extension.  Since the rubbish ATI drivers will only allow you to use exactly one of {OpenGL, Composite}, XGL is the only way to get both working, because it uses OpenGL to do the Composite extension.

You could run any of Poofyhairguy's (Breezy) eyecandy howto's on XGL.  These are the Knome (using kwin in gnome as the composite manager) guide, and... I forget the other one ;)

---

### Post by darkpark on 2006-07-12
Cool, thank you!   I guess I'm off to install XGL/Compiz.  :)

---

