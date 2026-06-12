---
title: "Reset keyboard shortcuts?"
date: 2008-05-30
forum: General Help
---

### Post by george9233 on 2008-05-30
Hello. 

Is there a way to reset the gnome keyboard shortcuts to default setting?

Thanks.

---

### Post by Brucevdk on 2008-05-31
This might not work (and is sort off a 'last resort' approach) so you'll want to backup your entire ~/.gconf folder before trying this. Note that I haven't actually tried this myself.

If you want to reset the keyboard shortcuts remove the directories *global_keybindings, keybinding_commands, window_keybindings* from the directory *~/.gconf/apps/metacity* and logout/login (not necessary persé, but it sure is the easiest route).

---

### Post by george9233 on 2008-05-31
Thanks for you idea.

---

### Post by mathewd on 2011-02-11
> **Brucevdk said:**
> This might not work (and is sort off a 'last  resort' approach) so you'll want to backup your entire ~/.gconf folder  before trying this. Note that I haven't actually tried this myself.

If you want to reset the keyboard shortcuts remove the directories *global_keybindings, keybinding_commands, window_keybindings* from the directory *~/.gconf/apps/metacity* and logout/login (not necessary persé, but it sure is the easiest route).

just ran into a similar problem. keybindings were behaving weirdly after  i played with them (and the backspace-technique wasn't resetting their  behavior correctly).

tried this suggestion, and solved the problem in 30 seconds :-) thanks bruceydk! :grin:

---

### Post by DavidBooth on 2013-01-11
See [http://askubuntu.com/questions/17626/how-can-i-restore-default-keyboard-shortcuts/240103#240103](http://askubuntu.com/questions/17626/how-can-i-restore-default-keyboard-shortcuts/240103#240103)

---

