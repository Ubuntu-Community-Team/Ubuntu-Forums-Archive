---
title: "No shortcut at Applications&gt;Wine after reinstall of wine"
date: 2008-06-01
forum: General Help
---

### Post by Xirowei on 2008-06-01
I recently do the following tasks:

1. Uninstall wine from Add/Remove.
2. Manually delete .wine folder.
3. Manually right click on "Applications" -> Edit Menus -> Select Wine and Delete the Wine shortcut.
4. Reinstall wine.

My problem is after reinstall wine, there is no wine shortcut appear at Applications -> Wine. How should i fix this problem?

---

### Post by ibuclaw on 2008-06-01
Go into the following directories in the terminal
[LIST]
[*]1) ~/.local/share/desktop-directories
[*]2) ~/.local/share/applications
[/LIST]
Find all the "**.desktop"** files related to WINE and open them with nano.

Now append the files so this line gets changed
```
NoDisplay=true
```
To this
```
**NoDisplay=false**
```

Press "**Ctrl+W**" to search for it in nano.

Regards
Iain

---

### Post by abanglek on 2010-11-14
this thread is sooooo loooong time ago, but for who have similar prob

edit main menu

click Revert

your wine menu will come back

---

