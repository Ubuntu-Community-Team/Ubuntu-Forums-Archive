---
title: "Strange problems with Gnome-art"
date: 2007-01-24
forum: General Help
---

### Post by swx- on 2007-01-24
When using gnome-art I get these messages:

- when starting: 

> 
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed


After gnome wallpaper section download:

> 
AM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/rexml/encoding.rb: line 37
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 37
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 37
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 37
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 37
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 37
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;

 
When trying to navigate from one section to another:

> 
/usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132: warning: GRClosure invoking callback: already destroyed


And this is not better with the Splash screen utility enclosed with gnome-art. Ive been searching all over the web and finding only briefs occurence to this problem. Can help help me  find a fix for this bug?

Thank you

---

### Post by adipl on 2007-03-09
I have the same problem

---

### Post by mrajaa on 2007-06-20
I was searching on the web for this problem and bumped into this thread.  Since I fixed the problem, I wanted to share it so someone else benefits.  It was fixed when I installed ruby-gnome2:

"sudo apt-get install ruby-gnome2"

---

