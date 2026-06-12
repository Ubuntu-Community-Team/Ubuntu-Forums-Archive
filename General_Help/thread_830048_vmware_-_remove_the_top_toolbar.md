---
title: "vmware - remove the top toolbar"
date: 2008-06-15
forum: General Help
---

### Post by mat28590 on 2008-06-15
okay so I know this is just being fussy, but is there a way to get rid of the toolbar at the top of the window, NOT when its maximised, I mean theres two menu's "Devices" and "Player" in the top left that I would like to remove. 

I know this is a weird request because the menus are needed to connect devices and what not, but I don't need to connect any devices in the foreseeable future.

Any thoughts on how to hide these menus?

---

### Post by dexo on 2008-11-28
[http://communities.vmware.com/message/732679](http://communities.vmware.com/message/732679)

It's possilbe on Windows to make the bar disappear by editting the preferencese.ini on the ACE instance's end-user system adding:

C:\Documents and Settings\<username>\Application Data\VMware\preferences.ini

pref.vmplayer.fullscreen.nobar = "TRUE"

---

### Post by dexo on 2008-11-28
Well here is solution for maximized:

[http://communities.vmware.com/message/732679](http://communities.vmware.com/message/732679)

It's possilbe on Windows to make the bar disappear by editting the preferencese.ini on the ACE instance's end-user system adding:

C:\Documents and Settings\<username>\Application Data\VMware\preferences.ini

pref.vmplayer.fullscreen.nobar = "TRUE"

---

