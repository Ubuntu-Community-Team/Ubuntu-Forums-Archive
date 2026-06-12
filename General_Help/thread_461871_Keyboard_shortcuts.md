---
title: "Keyboard shortcuts"
date: 2007-06-02
forum: General Help
---

### Post by kenmiles on 2007-06-02
I am running Ubuntu 6.10.
Can anyone please tell me if there is a way to assign keyboard shortcuts to custom programs or am I limited to the shortcuts in the system-preference-keyboard shortcus list.
Thanks in advance for any help,

Kenneth.

---

### Post by Brucevdk on 2007-06-02
For Metacity (and several other window managers) you can use *gconf-editor*. The settings are located at */apps/metacity/global_keybindings* and */apps/metacity/keybinding_commands*.

Use the run_command series for running custom programs.

---

