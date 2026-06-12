---
title: "Menu Editor: renaming a menu item and changing its icon"
date: 2020-01-31
forum: General Help
---

### Post by orthoducks on 2020-01-31
I have installed Menu Editor and created a new menu directory and a launcher in the directory. Only problem is that Menu Editor names them something like "New directory" and "New launcher," which are not very useful names.

I found that when I select a directory or launcher its name appears in the righthand panel, and if I click the name it turns into an edit box. I think I should be able to change a name by editing it in the edit box and pressing Enter. But that doesn't work. When I press Enter the box goes away and the original name reappears in its place. Nothing changes.

Is there some obscure button I must click to make this work?

The other problem I have is that I want to change the icon that represents the menu item, and I can't find a way to do it. The answer may be that this can't be done directly; I have to change the icon that represents the executable that the launcher is based on. But the executable is a .desktop file, and Ubuntu assigned it an orange diamond-shaped default icon when I created it; I can't find a way to change *that.*

---

### Post by CatKiller on 2020-01-31
You're making it harder for yourself than you need to. The launchers are just text files. The ones you've created for yourself will be in your Home folder, probably in ~/.local/share/applications. The format is pretty straightforward, and there's a specification for them, or you can just drag and drop any others into a text editor to see how they work. You can either specify the full path to your image file for the icon or simply use the name from the icon theme - again, just look at some of the others to see how that works.

---

