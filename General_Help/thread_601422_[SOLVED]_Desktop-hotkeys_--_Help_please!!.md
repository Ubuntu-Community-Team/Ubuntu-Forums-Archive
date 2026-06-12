---
title: "[SOLVED] Desktop-hotkeys -- Help please!!"
date: 2007-11-03
forum: General Help
---

### Post by perixx on 2007-11-03
Please help... 

I can't change Xfce's **default Hotkeys** under > Applications > Settings > Keyboard Settings > [Tab] Shortcuts

they're greyed out and I cannot find a config file where those are being set!

I want to create a 'Ctrl-Alt-Del'-Hotkey for the 'xfce4-taskmanager' to show up and I believe it would interfere with a system-Hotkey.

I also tried to start 'gconf-editor' and create an own shortcut under 
> apps > metacity > keybinding_commands / global_keybindings > command_1
but I couldn't even get the command <Control><Alt>t to work...

;[[


perixx

---

### Post by strabes on 2007-11-03
You need to make a new keyboard shortcut theme. I don't remember exactly where this option is, but it's somewhere in the keyboard shortcuts window.

---

### Post by perixx on 2007-11-03
Thx, strabes! 

You put me back on the right track -- I was so close, yet so far away :D

> Applications > Settings > Keyboard Settings > [Tab] Shortcuts

Just had to "Add" a new Shortcut-Profile and replaced the "xflock4" -- GREAT!


Now, you don't happen to know, how to lock the 'Ctrl + Alt + Backspace' Hotkey, do? I'd really like to disarm that one!!


perixx

---

### Post by perixx on 2007-11-04
Please, someone knows how to lock the 
"Ctrl+Alt+Backspace" Hotkey under Xfce??


perixx

---

### Post by perixx on 2007-11-07
Well, partially solved so far...

(maybe refer to my other post regarding CTRL+ALT+BACKSPACE and post there, if you got a solution...)


perixx

---

