---
title: "Ctrl-Alt-Del reboot :("
date: 2007-11-08
forum: General Help
---

### Post by nave.notnilc on 2007-11-08
When at a terminal I can hit Ctrl-Alt-Del and make my box reboot.  How can I disable this?
I'm running 7.10.

---

### Post by jgoguen on 2007-11-08
Open a Terminal (Applications -> Accessories -> Terminal) and use these commands:
```

gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

Now, Ctrl+Alt+Del brings up the system monitor.

---

