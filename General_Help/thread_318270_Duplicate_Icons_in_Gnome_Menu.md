---
title: "Duplicate Icons in Gnome Menu"
date: 2006-12-13
forum: General Help
---

### Post by NetworkGuy on 2006-12-13
Hi All,

I have a problem that I can't figure out how to fix.  I have two icons of the same game listed in my menu.  I think I used Alacarte instead of the menu layout option in preferences, now I can't figure out how to remove the duplicate icon.  

Using Alacarte and the menu layout options doesn't do it and I can't find where the actual files are that make the gnome menu system so I can just remove the wrong one.

How can I remove this duplicate icon?

Thanks.

---

### Post by xabbott on 2006-12-13
In Edgy, right click the menu and select 'Edit Menus'. Now go to the launcher in question, right click it, select delete.

---

### Post by NetworkGuy on 2006-12-13
thanks for the quick reply.

I tried that, the entries are still there.

---

### Post by David Corrales on 2006-12-13
Check to see if you have an atomic tanks .desktop file on your home folder. If there's one, move it to another folder or rename it to see if it helps.
Just a longshot :)

---

### Post by NetworkGuy on 2006-12-13
No, it's not there either.

Does anyone know where the actual menu system files are for gnome?

---

### Post by NetworkGuy on 2006-12-13
Found it.   

i finally did a locate on the right key name and found it in ~/.local/share/applications

Thanks all for the assist.

---

