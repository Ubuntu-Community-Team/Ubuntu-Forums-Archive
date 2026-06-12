---
title: "[SOLVED] how to show the drive icon on desktop?"
date: 2008-05-14
forum: General Help
---

### Post by elidoperezmd on 2008-05-14
hey all

i dont know why it is not doing it any more after hardy, but whenever i used to plug the phone, ipod, pen drive or any other right away the icon would show on the desktop, which was great. but is not happening any more. how can i make it do this?

thanks for the replies

---

### Post by bmac on 2008-05-14
Open "Configuration Editor"
Select:
apps/nautilus/preferences
check box for "show_desktop"

---

### Post by r76 on 2008-05-14
for configuration editor, type
```
gconf-editor
```
in the terminal (in Applications, Accessories)

Look out for the trash and home icons in that dialog box - you might find find them useful too.

---

### Post by mandrill on 2008-05-14
> **r76 said:**
> for configuration editor, type
```
gconf-editor
```
in the terminal (in Applications, Accessories)

Look out for the trash and home icons in that dialog box - you might find find them useful too.
Better yet, Config. editor > apps > Nautilus > desktop....choose what you want on your desktop there....

---

### Post by r76 on 2008-05-14
Where is this config editor I have heard so much about?

---

### Post by mandrill on 2008-05-14
> **r76 said:**
> Where is this config editor I have heard so much about?

System>Preferences>Main Menu>System Tools....its the very first choice.

edit: sorry, I gave you Gnome instructions.

---

### Post by disturbedite on 2008-05-14
i wish they would reimplement this for kde4 already...
maybe someone will make a plasmoid to do it?

---

### Post by drs305 on 2008-05-14
You can use the command line to show or hide your drives. I've made shortcuts on my panel to do this. 

The command line inputs to show (1st) and hide (2nd) the drives on the Desktop are:
Show:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible true
```

Hide:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible false
```

To make a panel shortcut, just rt click on the panel, select Add to Panel, Custom Application Launcher, pick a name and icon and paste the command into the command window.

---

### Post by r76 on 2008-05-15
> **mandrill said:**
> System>Preferences>Main Menu>System Tools....its the very first choice.

edit: sorry, I gave you Gnome instructions.

No problem, I found it and ticked the system tools box but now where is it on the menu?

[EDIT] never mind, it's not on the menu because the checkbox doesn't stay checked - I guess that's another issue.

[EDIT, again...] Got it working!, so you have to go to system tools box in the left column, not check the system tools box in the right column.  Just as well there is a CLI command for morons like me!

---

### Post by Gina on 2008-05-15
Well... I added config editor to the menus and checked out nautilus - show-desktop is already on and so is auto-mount but my partitions and external drives still don't auto mount and show on the desktop (they used to).

---

### Post by mandrill on 2008-05-15
> **Gina said:**
> Well... I added config editor to the menus and checked out nautilus - show-desktop is already on and so is auto-mount but my partitions and external drives still don't auto mount and show on the desktop (they used to).

system tools>apps>nautilus>desktop....inside are choices for what to show and/or not on the desktop....remember this is for gnome, kde is probably slightly different....good luck!

---

