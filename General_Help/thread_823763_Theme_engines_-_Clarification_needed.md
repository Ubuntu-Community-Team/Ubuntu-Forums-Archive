---
title: "Theme engines - Clarification needed"
date: 2008-06-09
forum: General Help
---

### Post by abh83 on 2008-06-09
I found quite a few themes that I really like but they all require the Aurora theme engine.

I currently use the default Ubuntu engine (GTK2.0... i think?).

Is it possible to have multiple theme engines installed on one system? How easy is it to switch between them? Is there anything else I should know before installing a theme engine? Is there any risk involved when installing a new engine?

I currently have Ubuntu set up just the way I like it and everything is running error free.

Thanks in advance.

---

### Post by fedex1993 on 2008-06-09
yes actually the aurora theme engine should be installed already. Just download the file and use the apperance program to install the theme

---

### Post by abh83 on 2008-06-09
so Ubuntu uses the Aurora theme engine then?

---

### Post by spupy on 2008-06-09
There is no problem in installing a new theme engine. The theme engine is the code that draws the widgets (buttons, menus, text fields...). Ubuntu default theme uses the clearlooks theme engine, i think. 
It looks like this:
---------------------------
gtk - provides the widgets, how you can create them, place them, structure them in a window.
---------------------------
theme engine - draws the widgets - draw a line, then vertical line, horizontal line, vertical one - a button!
---------------------------
theme - used to pass some optional parameter to the theme engine - like color of the widgets, a gradient, how rounded the corners are, etc.
---------------------------

It is even possible that one theme uses more than one engine!

---

### Post by abh83 on 2008-06-09
okay thx a lot! will give it a try tomorrow morning!

---

