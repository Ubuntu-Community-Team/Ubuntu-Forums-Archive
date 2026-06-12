---
title: "How to show menu bar in new gnome terminal"
date: 2022-04-20
forum: General Help
---

### Post by Tom_Carr on 2022-04-20
The gnome terminal that comes with Jammy is Version 3.44.0 for GNOME 42.  It does not have the menu bar and I don't see any way to add it.  Is there a way?  If not, can you suggest another terminal that does have the menu bar?

---

### Post by ajgreeny on 2022-04-20
I have no idea how well or badly it will integrate with the gnome DE of Ubuntu but xfce4-terminal has an option to show toolbar and menubar and xfce is a gtk based DE just like gnome,

I have not used gnome for a long time now with the "poor" GUI, as far as I'm concerned, being one of the main reasons for me finding it not to my taste.

---

### Post by tea for one on 2022-04-20
You can edit a shortcut to toggle on/off the menu bar for Gnome Terminal 3.44.0.

Open terminal > Right click > Preferences > Shortcuts > View > Hide and Show menubar

---

### Post by tea for one on 2022-04-20
I forgot to include another fix.

This command will display the menubar permanently:-
```
gsettings set org.gnome.Terminal.Legacy.Settings headerbar false
```
Close the terminal and open it again, the menubar should be visible.

To reverse the setting, change false to true.

---

### Post by Tom_Carr on 2022-04-24
> [COLOR=#000000]You can edit a shortcut to toggle on/off the menu bar for Gnome Terminal 3.44.0.[/COLOR]

[COLOR=#000000]Open terminal > Right click > Preferences > Shortcuts > View > Hide and Show menubar[/COLOR]

When I do that, to the right of "Hide and show menubar" it says disabled.  Clicking on it doesn't do anything.

---

### Post by Tom_Carr on 2022-04-24
> [COLOR=#000000]This command will display the menubar permanently:-[/COLOR]
[COLOR=#000000]Code:
gsettings set org.gnome.Terminal.Legacy.Settings headerbar false[/COLOR]
[COLOR=#000000]Close the terminal and open it again, the menubar should be visible.[/COLOR]

[COLOR=#000000]To reverse the setting, change false to true.[/COLOR]

That doesn't work

---

### Post by tea for one on 2022-04-24
> **Tom_Carr said:**
> That doesn't work

When you run the command in the terminal and it doesn't work, can you provide some more details.
Is there any terminal output to show what happened?

---

### Post by Dennis N on 2022-04-24
Just right-click inside the terminal window. In the context menu is a box that says "Show Menubar"

---

### Post by tea for one on 2022-04-24
> **Dennis N said:**
> Just right-click inside the terminal window. In the context menu is a box that says "Show Menubar"
Yes, that is fine for a single terminal session but it does not display the menu bar permanently.
You have to use gsettings or dconf to display the menubar whenever you open the terminal.

---

### Post by Dennis N on 2022-04-24
> **Tom_Carr said:**
> When I do that, to the right of "Hide and show menubar" it says disabled.  Clicking on it doesn't do anything.
Click on 'disabled' and when you see "set new accelerator" you can enter a shortcut key.

---

