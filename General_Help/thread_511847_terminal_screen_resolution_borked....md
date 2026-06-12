---
title: "terminal screen resolution borked..."
date: 2007-07-28
forum: General Help
---

### Post by SSamiK on 2007-07-28
I've just installed Feisty on a Fujitsu Simens Amilo Notebook and stumbled upon a problem...
When changing to a terminal by pressing "Ctrl+Alt+F?" the screen becom almost unreadable. It sort of split in two, and the left part flickers over to the right making it unreadable. Looks like the resolution is to small for the widescreen display and it's becoming streched and distorted. 
Is there a way to change the screen resolution so this wont happen? 


PS:
It looks just fine when inside Gnome, and i've installed the needed openchrome drivers.


SOLVED: had to edit /boot/grub/menu.lst and pass a vga=xxx to the kernel line. In my case "vga=0x03b8" to get 1280x800 as my resolution.

---

