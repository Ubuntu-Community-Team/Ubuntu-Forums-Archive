---
title: "assigning a hotkey to &quot;on top&quot;? focus window for maya"
date: 2006-10-27
forum: General Help
---

### Post by tempo500 on 2006-10-27
how can i assign a hotkey to the menu item located on the left side of the program-bar ""on top". i am using gnome... thanx philip

---

### Post by TheBlackNoodle on 2006-10-27
I'm not at all sure what you're talking about, but to assign custom hotkeys in gnome 2.14, you should start the Configuration Editor (a.k.a. gconf-editor). Run it in the terminal if it's not available in a drop-down menu. Hit CTRL-F, and search for "keybindings." In your search results click /apps/metacity/global_keybindings. You're able to edit actual keybindings here. If you look in the left pane, you can click on keybinding_commands to actually make custom hotkeys. If you do that, then run_command_# in global_keybindings will corresponding to command_# in keybinding_commands.

Note again that this is for gnome 2.14... I assume it's similar in Gnome 2.16.

---

