---
title: "Is there a way to add the &quot;Main Menu&quot; to the right-click desktop context menu?"
date: 2008-06-08
forum: General Help
---

### Post by gohanssjn on 2008-06-08
i want to completely remove the panel from the top of the screen.  To do this, I'd like to be able to just right click on the desktop, and have a menu option in my context menu that has things like "Change Desktop Background."

Can this be done?

---

### Post by pmaconi on 2008-06-08
You can do that by using the Openbox window manager instead of metacity/compiz. Here's a howto: [http://urukrama.wordpress.com/openbox-guide/]("http://urukrama.wordpress.com/openbox-guide/")

---

### Post by gohanssjn on 2008-06-08
Well shoot, the rest of the stuff I have going is in Compiz.  No other way?

---

### Post by gohanssjn on 2008-06-09
Guess I don't HAVE to have it, I just hate that gap at the top of the screen when I maximize a window...

---

### Post by Forlong on 2008-06-09
You know you can autohide the GNOME panel? :)

---

### Post by alex_anthony on 2008-06-09
there's a new compiz fusion plugin to do that, but it is only in git atm (if that)
alternatively, an AWN plugin if you're using it, or a screenlet which does this

---

### Post by gohanssjn on 2008-06-10
Ah, maybe I'll do it with AWN.

And yes, I know I can auto-hide the panel, but it still leaves something close to a 5px gap when maximizing windows.

---

### Post by p-w on 2008-06-10
Hi there, you can change the minimised size of the panel in gconf-editor.  Go to apps->panel->toplevels->top_panel_screen0 and change auto_hide_size to 0.  You can also change the animation settings and the delay before hiding here.

---

