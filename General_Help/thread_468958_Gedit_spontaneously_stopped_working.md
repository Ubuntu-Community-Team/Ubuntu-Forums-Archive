---
title: "Gedit spontaneously stopped working"
date: 2007-06-09
forum: General Help
---

### Post by polt on 2007-06-09
Hello Everyone,

I have been using gedit just fine on Feisty Fawn.  Today, I was trying to edit an htm file and the program wouldn't even open it.  It will open a new document, but whenever I try to use gedit to open any other documents, txt, htm, or otherwise, I get these errors:
> 
gedit: /usr/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

(gedit:6904): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GeditView' has no property named `highlight_current_line'
gedit: symbol lookup error: gedit: undefined symbol: gtk_source_view_set_highlight_current_line


Any ideas?  I tried uninstalling and reinstalling gedit, to no avail.

---

### Post by polt on 2007-06-09
It seems I get the same library error when trying to use another text editor, Gvim.  I found some people discussing this in relation to VMWare, but I don't think I have VMware.

---

### Post by polt on 2007-06-09
Okay, I went through Synaptic and uninstalled all of the outdated software/libraries as well as removing all config files that no longer had a program attached to them.  That seems to have solved the first error message.  I am still getting the Glib one though.

---

### Post by polt on 2007-06-09
Fixed!  The problem had to do with mono and libgtksourceview, which I reinstalled.  This thread had the answer:
[http://ubuntuforums.org/showthread.php?t=213093](http://ubuntuforums.org/showthread.php?t=213093)

---

