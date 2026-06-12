---
title: "Evince/ gtk problem"
date: 2015-03-04
forum: General Help
---

### Post by howard-gilbrt on 2015-03-04
When I try to start Evince from  deskyop icon it appears briefly then disappears.

If I start from a command line I get "~$ evince

(evince:2950): Gtk-CRITICAL **: gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed

(evince:2950): Gtk-CRITICAL **: gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed
Segmentation fault (core dumped)"

However, if I open a .pdf file from file manager it behaves OK.

---

### Post by ajgreeny on 2015-03-04
Do you have evince or evince-gtk installed as the application?

I did have evince installed but I have just changed the installed package to evince-gtk and so far I can see no difference between them, nor do I get any errors when opening them in terminal.

---

### Post by howard-gilbrt on 2015-03-06
Thanks  ajgreeny.  I had evince, I changed to  evince-gtk it made no difference to my problem.

---

### Post by dino99 on 2015-03-06
you probably get that error due to some installed buggy plugin(s)
[http://www.gtkforums.com/viewtopic.php?p=6516](http://www.gtkforums.com/viewtopic.php?p=6516)

try to deactivate/deinstall those plugins, then reinstall them one by one to find out which one might be blamed

---

