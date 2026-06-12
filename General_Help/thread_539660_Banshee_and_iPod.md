---
title: "Banshee and iPod"
date: 2007-08-31
forum: General Help
---

### Post by gavinjb on 2007-08-31
Hi,

Sorry if this has been asked before, but I cant find anything from searching the forum, but is it possible to change the default so that Banshee opens when I plug my iPod into Ubuntu and not Rhythmbox.

Thanks,


Gavin,

---

### Post by dashnak on 2007-08-31
Yes.
Go to System->Preferences->Something about portable units or so (mine's in spanish)
The go to the multimedia Tab, and you will find what you're looking for,

---

### Post by ninehrcoma on 2007-08-31
System->Preferences->Removable Drives and Media and select the "Multimedia" tab.

---

### Post by ninehrcoma on 2007-08-31
Additionally, you could do it manually via gconf-editor or edit the file directly (~/.gconf/desktop/gnome/volume_manager/%gconf.xml).

First run gconf-editor.

The gconf key is under desktop/gnome/volume_manager. Once you have expanded those options in the tree, scroll down on the right side a bit and you will see the key that matches "autoipod_command". You can double-click the key and put the name of any app or script you want.


Of course this sort of goes against the simplicity of opening a configuration window from preferences and checking a box... I must be bored today.

---

### Post by gavinjb on 2007-08-31
Thanks, changed it in Removable Drives and Media, I knew I had seen the setting before, just couldn't remember where.

---

