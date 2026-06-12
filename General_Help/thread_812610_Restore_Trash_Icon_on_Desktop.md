---
title: "Restore Trash Icon on Desktop"
date: 2008-05-30
forum: General Help
---

### Post by vkpardava on 2008-05-30
Restore Trash Icon
I tried to change the trash icon on my current theme to one from another theme because I like everything in the current theme except for the trash icon. But when I changed it I had not taken into consideration the fact that the icon has to be able to be variable based on whether or not something is in the trash and so I ignorantly set it to a fixed icon. Once I made the realization that I did not know enough about how that icon works, it was too late. Now my icon does not change based on whether it is empty or not and changing the custom icon theme or the theme in general does not make a difference. Now I just want to put it back to the way it was an forget about it.

Does anyone know how to put it back the way it was so that my trash icon uses the trash icon from whatever icon theme is in place and so that it responds to content, or lack thereof?

---

### Post by Forlong on 2008-05-30
Right-click on the trash icon and chose **Properties**.
Then click on the (custom) icon and instead of selecting one from your hard-drive, click on **Revert**.

---

### Post by Premium_User on 2008-05-30
I'm having a problem with the trash icon on my desktop as well. 

My problem is just a bit different. The icon for the trash keeps disappearing from the panel on the bottom side of the desktop. 
It just simply vanishes! 

The only way I can get it to reappear is to delete the panel. Reboot Hardy, rebuild the panel, and hope when I put the trash icon back on the panel with the add to panel tool, that is doesn't vanish again.

I tried Forlong's suggestion to right click on the trash icon and use the properties dialog, but that option doesn't seem to exist when I right click the trash icon.  

I would send a screen shot of the options, but the system won't let me take one with a dialog function open.

I'll list them from the top:

Open 
Empty Trash
Help
About
Remove from panel
Move
Lock to panel

Am I missing a properties option in the right click dialog on the trash icon from the panel bar?

---

### Post by Forlong on 2008-05-31
> **Premium_User said:**
> Am I missing a properties option in the right click dialog on the trash icon from the panel bar?
No you're not. Trash panel applet is a totally different thing than the trash icon on the desktop.

---

### Post by Premium_User on 2008-05-31
> **Forlong said:**
> No you're not. Trash panel applet is a totally different thing than the trash icon on the desktop.

No doubt it is. But nowhere did the op specify that he had a trash icon on
his desktop. 

Forlong said;

# "Right-click on the trash icon and chose Properties.Then click on the (custom) icon and instead of selecting one from your hard-drive, click on Revert."

In the default install of hardy on this machine there is no trash icon on the desktop! Only on the panel bar is one to be found. Perhaps you should keep that in mind.

I figured out how to put one on the desktop by utilizing the configuration
editor(which is not enabled to start with) in the applications menu by going to the section /apps/nautilus/desktop/trash_icon_visible and checking it.

If anyone else is reading this and needs to enable the configuration editor
you must right click on the applications section of the panel bar and click edit menus. On the left side click sytem tools to highlight it and then look on the right side for the configuration editor and place a check mark in the appropriate box and select close.

On the top panel go to applications/system tools/ ,click on configuration editor.
Then browse to the aforementioned path to make your adjustments.
Also there is a nifty bookmark section in the editor which lets you
bookmark the section for speedier access in the future.

Anyhow, there is still nothing you can do even with the trash icon on the desktop to keep the icon from disappearing from the panel bar that I can see.

---

### Post by Thras0 on 2010-11-26
> **Forlong said:**
> Right-click on the trash icon and chose **Properties**.
Then click on the (custom) icon and instead of selecting one from your hard-drive, click on **Revert**.
i just wanted to say thanks for the info.i changed that icon so many times that when i wanted it back to default , i didn't know how to restore it. :)

---

