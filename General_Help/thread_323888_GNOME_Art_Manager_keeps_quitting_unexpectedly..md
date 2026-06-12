---
title: "GNOME Art Manager keeps quitting unexpectedly."
date: 2006-12-22
forum: General Help
---

### Post by Antarctica on 2006-12-22
I installed GNOME Art Manager today, and for anybody who knows Art Manager, when I go to the Art menu and choose a category, sometimes the program crashes and quits unexpectedly.  I'm pretty sure that the program does not have a bug, but I was wondering, is the site art.gnome.org having problems?

---

### Post by raul_ on 2006-12-22
try starting the program through the terminal and when it crashes, it should produce an error..at least you'll know what the problem is

PS: I put my money on "segmentation fault"

---

### Post by Antarctica on 2006-12-23
Well it's working kinda.  I can deal with it for now.

---

### Post by arijarot on 2007-06-04
> **raul_ said:**
> try starting the program through the terminal and when it crashes, it should produce an error..at least you'll know what the problem is

PS: I put my money on "segmentation fault"

I have the same problem; gnome-art quits unexpectedly when I try to dl something (e.g., splash screen). here is the terminal output:

```

: gnome-art
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
/usr/lib/ruby/1.8/rexml/encoding.rb: line 31
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 2: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/rexml/encoding.rb: line 31
   Gtk-WARNING **:Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand is not supposed to be an entity, escape it as &amp;
/usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132: [BUG] Segmentation fault
ruby 1.8.5 (2006-08-25) [i486-linux]

Aborted (core dumped)

```

you may be right, but what does that mean (e.g., segmentation fault)?

---

### Post by STICKMANRADIO on 2007-06-07
I just started using Art Manager today. Downloaded a couple Backgrounds and one splash screen and then the program would keep closing.

I went and chose "File > Delete Cached Files" and was back in business. Hope it works for you as well.

---

### Post by arijarot on 2007-06-08
> **STICKMANRADIO said:**
> I just started using Art Manager today. Downloaded a couple Backgrounds and one splash screen and then the program would keep closing.

I went and chose "File > Delete Cached Files" and was back in business. Hope it works for you as well.

I tried the suggestion and it didn't work; same issue. since this is a bug, can't it be reported (I'm not sure of the process)?

---

### Post by weedwacker on 2007-06-09
I'm having the same problem.  When I click "Download Only" the Art Manager quits.

I had one case of downloading that I thought was successful, but my Wallpaper folder was empty--- no download of the wallpaper.

I did a uninstall and reinstall of Art Manager, but still quits on the "Download Only".

Somethin' wrong in River City!  :(

---

### Post by az_s_za on 2007-07-04
Same problem here.  I open gnome-art, go to 'art', then select any option.  It then starts to download themes from the selected category, but always locks up before the download finishes.

I have tried the suggestion in this thread, and solutions offered in similar threads, but still have this problem.

Ideas anyone?

---

