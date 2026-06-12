---
title: "compiling mail-notification 4.0 - which gnome libs?"
date: 2007-02-24
forum: General Help
---

### Post by jasonv on 2007-02-24
in my latest attempt to compile mail-notification 4.0, i'm running into this error:

> 
checking for GTK+ - version >= 2.6.0... yes (version 2.10.6)
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... no
configure: error: unable to find the GNOME libraries
~/mail-notification-4.0$ 


which gnome libs, I ask? i've installed as many as I could reason to be related, it's upwards of 100MBs so far. there's even a synaptic entry that just says, "The GNOME libraries".

any help would be greatly appreciated.

---

### Post by energiya on 2007-02-25
try [this]("http://www.ubuntuforums.org/showthread.php?p=2201673").

---

### Post by carbonic on 2007-02-27
I got the same problem and by looking at the config.log file I get this error:> 
configure:22854: $PKG_CONFIG --exists --print-errors "gthread-2.0 gconf-2.0 >= 2.4.0 libgnomeui-2.0 >= 2.8.0 gnome-vfs-2.0 libglade-2.0 eel-2.0 >= 2.6.0 bonobo-activation-2.0 libxml-2.0 libnotify"
Package eel-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `eel-2.0.pc'

But can't find eel-2.0

---

### Post by jasonv on 2007-02-27
search for libeel2

:-)

---

### Post by Darkside63 on 2007-03-02
Well, could be anything actually :)

I compiledt thos afternoon and spent quite some time until finding out, that libGmime was missing :)

---

