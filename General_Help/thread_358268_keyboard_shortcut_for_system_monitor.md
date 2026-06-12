---
title: "keyboard shortcut for system monitor"
date: 2007-02-10
forum: General Help
---

### Post by mpgarate on 2007-02-10
I wanted to set a keyboard shortcut to run the system monitor when I press control+alt+delete. How would I go about doing this? It is not in the keyboard shortcuts page under system preferences.

---

### Post by Gibbs on 2007-02-10
Check out [http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/)

The command is **gnome-system-monitor** for the system monitor.

---

### Post by xkendrax on 2007-08-04
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_12 "gnome-system-monitor"
gconftool-2 --set --type string /apps/metacity/global_keybindings/run_command_12 "<Control><Alt>Delete"

---

