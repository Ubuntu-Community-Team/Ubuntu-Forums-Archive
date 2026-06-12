---
title: "Is there a way to edit these shortcuts in AmaroK?"
date: 2006-08-10
forum: General Help
---

### Post by boom2k1 on 2006-08-10
I would like to use my keyboard to control play/pause, etc in AmaroK. However, by default the play/pause key does not have shortcut to control it and other shortcuts are associated with the windows key which I already remapped to another function.

How would I reassign these shortcut keys? THanks!

---

### Post by boom2k1 on 2006-08-10
I have found a solution.

It involves using xbindkeys-config

In Terminal, type: xbindkeys-config

in this GUI interface, just assign your desired key to the command 

amarok -pause

for re-play/pause function.

For other commands, you can open up Terminal and type

man amarok and read through the options.

i.e. 
amarok -s     stop
amarok -r     previous
amarok -p     play
amarok -pause pause(and replay)
amarok -f     next

---

### Post by orb9220 on 2006-08-10
Or you can install keytouch and import the keyboard file for yours even has specific amorak support.

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

---

