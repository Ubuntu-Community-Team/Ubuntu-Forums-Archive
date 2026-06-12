---
title: "Workspace Switcher Problem"
date: 2008-05-19
forum: General Help
---

### Post by pmaconi on 2008-05-19
I'm not sure what I did, but sometime today my workspace switcher applet stopped working. I can no longer click the applet to switch between workspaces, drag windows across workspaces, or use most of the compiz plugins to switch between them (ex: cube doesn't work). The only way that I can switch them is to use expo. 

Since the last time that I used it, I have changed my gtk theme, gdm theme, installed some icons, changed the cursor pointers, and set up AWN. Uninstalling AWN didn't fix it and I don't think any of the other changes could have possibly caused this. Any ideas?

---

### Post by pmaconi on 2008-05-20
I figured out the problem, sort of. Enabling Desktop Cube breaks the workspace switcher (and doesn't work at all). But disabling Cube and enabling Wall works fine. Does anyone know how to configure Hardy to use the cube?

---

### Post by bobjenkins on 2008-05-20
Try enabling 
Desktop cube, Desktop **PLANE** and Rotate Cube, I had this problem also this fixed it

Hope this helps!
Edit oh my bad, it was the other way around, Plane was messing it up I had to switch to Wall, sorry

If you want the cool cube and rotating with the mouse enable

Desktop Cube and
Rotate Cube
And try Viewport switcher (enables mouseleft+mouseright rotating)

then hold
Alt+Control+mouse1 and drag mouse
Alternatively press mouse1+mouse 2 (left and right mouse) at the same time then drag mouse

To make it cooler play around with the settings in compiz, under rotate cube> general tab increase the zoom

---

### Post by pmaconi on 2008-05-20
Thanks. I think that I forgot to enable rotate cube the first time around.

---

