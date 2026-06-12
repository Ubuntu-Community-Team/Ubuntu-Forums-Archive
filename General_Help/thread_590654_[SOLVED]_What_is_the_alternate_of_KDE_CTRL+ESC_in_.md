---
title: "[SOLVED] What is the alternate of KDE CTRL+ESC in GNOME"
date: 2007-10-24
forum: General Help
---

### Post by anantgowerdhan on 2007-10-24
Hi,

I recently switched from KDE (Kubuntu) to GNOME (Ubuntu) and I'm looking for ther alternative of Ctrl+Esc in GNOME. In KDE if you use this combination it opens a window with all the running processes/application that you can choose and kill. Please let me know how can i do the same in GNOME (Ubuntu)

Regards,
Anant

---

### Post by jshurst on 2007-10-25
You can hit Alt+F2 then type in   gnome-system-monitor.

I found this online if you want to assign it to Ctrl-Alt-Delete (I have not tried this so...)

[I]To get Ctrl-Alt-Del-shortcut to open System Monitor do this:

1. Open Configuration Editor (hit Alt-F2 and run gconf-editor).
2. Browse to apps/metacity/keybinding_commands
3. Set the command_1 to gnome-system-monitor.
4. Browse to apps/metacity/global_keybindings
5. Set run_command_1 to <Control><Alt>Delete
[/I]

Hope that helps
J

---

### Post by anantgowerdhan on 2007-10-25
Thanks alot, it worked but I would like to add something here is, when I used <Cntrol><Alt>Delete it didnt setup to open system monitor but when I used <Contro><Shift>Delete it worked. I assume its because <Control><Alt>Delete is already set for shutdown.

Regards,
Anant

---

