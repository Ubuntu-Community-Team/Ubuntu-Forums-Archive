---
title: "Trash icon missing on desktop"
date: 2007-03-03
forum: General Help
---

### Post by sdowney717 on 2007-03-03
Booted up today and it set the applet was corrupted and so I deleted it. Now how to get it back?
thanks

---

### Post by Aliarse on 2007-03-03
System tools > Configuration editor > Apps > Nautilus > desktop.



If Config editor isnt in your system tools menu, alt + f2 and type/copy "gconf-editor"

---

### Post by bapoumba on 2007-03-03
> **sdowney717 said:**
> Booted up today and it set the applet was corrupted and so I deleted it. Now how to get it back?
thanks
If running GNOME, you can right click on the panel and add it back.

---

### Post by sdowney717 on 2007-03-03
I tried to add to the panel and get this every time

the panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet",

do you want to delete the applet from your configuration?

---

### Post by sdowney717 on 2007-03-03
I tried the config editor, but see nothing about a trash icon.

Any more ideas?
thanks

---

### Post by sdowney717 on 2007-03-03
should there be a trash folder in the file system and where?
I was wondering if its gone. I do see a move to trash dialog when right clicking files.
Who knows where they end up now.

This happened on a boot, not like I did anything, but could some file/folder be gone??

---

### Post by sdowney717 on 2007-03-03
Also, I discovered if I try to create a new panel, I also get that same weird message.

---

### Post by sdowney717 on 2007-03-03
[http://debcentral.org/modules/newbb/viewtopic.php?topic_id=330](http://debcentral.org/modules/newbb/viewtopic.php?topic_id=330)

found it working now, config editor was the key, thanks.
BUT why did this happen??

---

### Post by sboutwell on 2008-02-26
Ok so have a tricky one going on now.  

The .Trash Directory Exists, The Trash Icon appears on the Panel, additionally when you run the gconf-editor and go into the System tools > Configuration editor > Apps > Nautilus > desktop the checkmark is in place.  But NO Icon still is appearing on the desktop.  Yep have rebooted and the other icon's for Computer, Network Servers and Home are there.  But the Trash seems to has run off.

Any ideas on how to fix this.  I'm not a total newb but this one has confused the HECK outta me.

---

