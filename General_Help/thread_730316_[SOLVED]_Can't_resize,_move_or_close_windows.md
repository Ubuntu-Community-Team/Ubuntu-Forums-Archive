---
title: "[SOLVED] Can't resize, move or close windows"
date: 2008-03-20
forum: General Help
---

### Post by bharkins on 2008-03-20
On my HP notebook, I had ENVY and compiz installed with problems. I uninstalled compiz via Synaptic and the Nvidia 3d driver via ENVY. When compiz was running I could not get any windows to operate using the mouse - resize, move, maximize, close, etc. The title bar was not there. After I uninstalled compiz and the Nvidia driver, the window problem remained. Any command to fix it?

---

### Post by doorknob60 on 2008-03-20
Press Alt-F2 and type this:
```
gtk-window-decorator --replace
```

---

### Post by bharkins on 2008-03-21
> **doorknob60 said:**
> Press Alt-F2 and type this:
```
gtk-window-decorator --replace
```

Didn't work. I have compiz running, so that started the problem. Windows go to the upper left corner and the title bar is tucked in behind the top panel, so can't grab the window to move,size or close.

---

### Post by bharkins on 2008-03-21
> **bharkins said:**
> Didn't work. I have compiz running, so that started the problem. Windows go to the upper left corner and the title bar is tucked in behind the top panel, so can't grab the window to move,size or close.

I have another odd issue - after reboot, the top panel disappears and only can be seen by moving the cursor to the top of screen. Then it appears and can be used, but then hides again after cursor removed. Nice if I wanted that "feature" but I don't. Again, compiz is running.

---

### Post by Therion on 2008-03-21
> **bharkins said:**
> I have another odd issue - after reboot, the top panel disappears and only can be seen by moving the cursor to the top of screen. Then it appears and can be used, but then hides again after cursor removed. Nice if I wanted that "feature" but I don't. Again, compiz is running.
For disappearing Panel:  Right-click on said Panel and disable "Auto Hide".

Regarding frozen windows/no window borders etc. ...

Navigate to: System/Preferences/Advanced Desktop Settings

Look for the **Window Decorations** plugin.  Is it enabled?  If not, enable it.  If it is, turn it "off" and then turn it right back "on".

Joy?

---

### Post by bharkins on 2008-03-22
> **Therion said:**
> For disappearing Panel:  Right-click on said Panel and disable "Auto Hide".

Regarding frozen windows/no window borders etc. ...

Navigate to: System/Preferences/Advanced Desktop Settings

Look for the **Window Decorations** plugin.  Is it enabled?  If not, enable it.  If it is, turn it "off" and then turn it right back "on".

Joy?

Fixed the panel hiding - thanks.

Windows Decorations: that did not work - windows still locked in left hand corner.

---

### Post by bharkins on 2008-03-23
Still looking for an answer on this one. Compiz removed, still have locked windows. In addition, the shutdown icon is also locked - can't restart or shutdown. There must be some residual function left from compiz after removal. I marked all installed compiz packages as remove for complete removal. I would have thought that would work. I expect there is a terminal command that would reset the Gnome desktop to normal conditions. Any help appreciated.

---

### Post by clanky on 2008-03-24
try right clicking on the desktop, then selecting the right hand tab (effects) and then select none.

I had the same problem and this fixed it,

Went back and selected custom again (with window decoration off) and it was OK.

---

### Post by bharkins on 2008-03-25
> **clanky said:**
> try right clicking on the desktop, then selecting the right hand tab (effects) and then select none.

I had the same problem and this fixed it,

Went back and selected custom again (with window decoration off) and it was OK.

The problem is even after uninstalling compiz. Thus the effects are set to none. Windows still locked in the corner. 

I'm looking for a Gnome desktop reset of some sort to get back to normal windows use.

---

### Post by bharkins on 2008-03-30
> **bharkins said:**
> The problem is even after uninstalling compiz. Thus the effects are set to none. Windows still locked in the corner. 

I'm looking for a Gnome desktop reset of some sort to get back to normal windows use.

This thread is NOT yet solved! It is a really annoying bug and only running on my HP notebook not the desktop machine. Any ideas?

---

### Post by der_perser on 2008-03-30
the only help i can give you is to reinstall the standard windowdecoration of gnome.
it seems like your system trys to start the windowdecoration of compiz, but it fails to load it because of an error or it does not exsist anymore.
i dont know exactly what you have to do because i use kde.

try to find information about gnomes standard windowdecoration
-reinstall it
-or try to activate it in the gnome control center

an other source for the problem could be that you have written an autostartup script or something similar for compiz/XGL (contains maybe also code telling your system to load a specific decoration). If you have written something like that, find it and remove it...

sry that i can't give you any more specific advises, but maybe it will help to find the source of the problem :(

---

### Post by bharkins on 2008-04-01
> **clanky said:**
> try right clicking on the desktop, then selecting the right hand tab (effects) and then select none.

I had the same problem and this fixed it,

Went back and selected custom again (with window decoration off) and it was OK.

This seems now solved. I went to Visual Effects, clicked Extras back on, let Ubuntu install the nvidia-glx-new, clicked back to None, and the Windows are now free - resize, move, minimize and close. On reclicking Extras, Windows are still "loose". Now I will go back and reinstall the Nvidia 3d driver (Envy), compiz and then Awn. It's sort of a long way around, but if windows are locked up as they were, the desktop is useless. Thanks for your input.

---

