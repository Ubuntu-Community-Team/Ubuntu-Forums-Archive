---
title: "Firefox 3 RC2 and SCIM"
date: 2008-06-05
forum: General Help
---

### Post by Malinthe on 2008-06-05
Hi guys,

I got Firefox RC2 and tried it out after extracting it. It loads fine and all but SCIM doesn't work with it.

I get this when I launch it:

[INDENT](firefox-bin:7140): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-scim.so: wrong ELF class: ELFCLASS64

(firefox-bin:7140): Gtk-WARNING **: Loading IM context type 'scim' failed[/INDENT]

What can be the problem? Any way to fix it? :confused:

---

### Post by life-on-mars on 2009-03-07
You're trying to use a 64bit scim together with a 32bit GTK application which obviously does not work. 

It should be possible to modify /etc/X11/xinit/xinput.d/scim so that it uses the 32bit scim library when a certain variable applies. Then you could invoke your application with a script that also exports that variable.

/etc/X11/xinit/xinput.d/scim-brigde contains code that should be helpful.

Or you could switch to a 32bit version of Ubuntu, which is what I was going to do anyway as there are too many applications that do not support amd64 Ubuntu.

---

