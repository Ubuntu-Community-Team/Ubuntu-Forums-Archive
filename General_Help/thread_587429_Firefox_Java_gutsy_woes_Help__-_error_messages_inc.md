---
title: "Firefox Java gutsy woes? Help  - error messages included -"
date: 2007-10-22
forum: General Help
---

### Post by episodic on 2007-10-22
Unfortuantly, I can't share the applet as it is on a private web - but in Firefox it takes about 1 minute to load the applet the whole time the system is frozen with the processor pegged at 100% (dual core athlon 64)

Same site - same java - epiphany loads the applet in like 2 seconds.

Is there some way that I can optimize firefox?

BTW - when launching firefox from the terminal. When I click on the applet, I get the following error messages in the terminal:

(<unknown>:8462): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:8462): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:8462): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed

(<unknown>:8462): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed


Can a guru help here?

---

### Post by episodic on 2007-10-22
Anyone?

---

### Post by euchrid on 2007-11-23
Sorry, no help, but I get (and have got) very similar problems - and can't find an answer. Firefox seems to freeze a lot on Java or Javascript pages, but it's very hard to tell exactly what's causing it... Hope someone can help with this!

---

### Post by _mrv on 2007-12-07
Hi,

Seems to happen on my machine too (Xubuntu 7.10) with latest updates. Pretty annoying.

 -mrv-

---

### Post by braacken on 2007-12-07
May want to double check that the site/domain is on the allowed list for installing software through firefox and that it is allowed to resize windows with an applet.

Firefox does have a lot of Java bugs, but if  you think about it, its for security purposes.  Maybe even check that the dom plugin that installs with firefox isn't contributing to the behavior.

query for particular settings in your about:config and et cetera

---

### Post by lemmy01 on 2008-01-09
Its a java bug!
Look at [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6624717]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6624717")
and vote for it

ralf

---

