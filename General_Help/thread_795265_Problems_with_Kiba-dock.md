---
title: "Problems with Kiba-dock"
date: 2008-05-15
forum: General Help
---

### Post by the.original.kermit on 2008-05-15
First I'm running Ubuntu 8.04 and am trying to install kiba-dock.  I've tried both of these install, and neither seems to be fixing my problem

[http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+won%27t+start](http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba+won%27t+start)

-and-

[www.kiba-dock.org](www.kiba-dock.org).

When I first installed, kiba-dock would kinda work, but clicking some categories under the settings would cause the settings window to lock up and turn gray.  The only way out was to force-quit.  I also was unable to add launchers to the dock.

Now I can't seem to get it to work at all.  When I run 

tonis@tonis-laptop:~$ kiba-dock

(kiba-dock:12586): GLib-GObject-WARNING **: cannot register existing type `GFileMonitor'

(kiba-dock:12586): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(kiba-dock:12586): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed

(kiba-dock:12586): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

My window move up to display the bar at the bottom where the dock should be, but the only there is the desktop.

Sorry, I'm new to Ubuntu, but any help would be appreciated.

---

### Post by the.original.kermit on 2008-05-15
Ok...

Tried completely uninstalling kiba again.  I deleted every file/dir with kiba in the name.  Reinstalled...same thing.

I tried reinstalling glib, and that also didn't have any affect.

Any suggestions??

---

### Post by the.original.kermit on 2008-05-15
No ideas?

---

### Post by the.original.kermit on 2008-05-18
Screw it, switched to awn dock.  Much better.  Doesn't have the physics bounce, but really that was only cool to play with, but realistically it's not the best because it rearranges your icons.

---

### Post by Tankerdog2002 on 2009-01-10
I don't know if this is helpful since this post is so old. However; I believe your problem can be solved by using the older version of Kiba. The new version is extremely buggy and requires too much from new users editing the sources.lst.

You can get the easy older version from "Swik kiba". Just download the .deb version and it will load with deb installer.

Get it here: [http://swik.net/kiba-dock](http://swik.net/kiba-dock)


Cheers,
Tank

---

