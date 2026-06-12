---
title: "Add Keyboard Shortcuts From Terminal"
date: 2007-05-14
forum: General Help
---

### Post by azarath metrion zinthos on 2007-05-14
[FONT="Trebuchet MS"]Does anyone know how to add a keyboard shortcut from the terminal (instead of through the GUI) via some text editor? Isn't there a location where the keyboard shortcut mappings are stored? Your help would be greatly appreciated.[/FONT]

---

### Post by utmark on 2008-05-22
I found this article helpful: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/")

Run **gconf-editor** from the terminal.
Navigate to **apps -> metacity -> global_keybindings**
Manually edit the **Values** associated with each action

-Mark

---

