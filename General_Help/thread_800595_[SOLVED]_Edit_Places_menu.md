---
title: "[SOLVED] Edit Places menu"
date: 2008-05-20
forum: General Help
---

### Post by pacrep on 2008-05-20
Is there a way to remove some stuff in the Places menu? Like Desktop, CD/DVD creator.

Opening home folder and right click Desktop in the side pane won't allow me to remove it. So anyone have any ideas?

---

### Post by Exsecrabilus on 2008-05-20
In the side pane, the stuff above the separator are system things that you cannot remove.

However, the files and folders below the separator are free for customization.

---

### Post by pacrep on 2008-05-20
Thx for clarifying that for me, no biggie but would've been nice to fully customize the menu.

---

### Post by Forlong on 2008-05-21
Those are hardcoded AFAIK, so it would only be possible when patching the source code.

---

### Post by reaperfh on 2009-05-08
bah! that sucks...
I mean why would anyone want a link to the desktop when they have it right in front of them... -.-
Thks anyway!

---

### Post by gseward on 2011-03-01
In my Places menu, in the panel, any location I pick takes me to "Appearance Preferences/Background", ANY place; Home, Documents, Download, Pictures, etc...
If I go to Nautilus Places, everything works fine, as do all the Nautilus Bookmarks. I tried removing the menu from the panel and adding it back, no change, problem still there.
Any ideas?

---

### Post by John Teisberg on 2011-03-18
I found the secret to editing the Places Menu. 
Find this file in your Home directory:
.gtk_bookmarks
Click it to open and you will see all the 'places' that show up.
Simply delete the ones you do not like and close the file.
Done.

---

### Post by krapp on 2011-06-20
> **John Teisberg said:**
> I found the secret to editing the Places Menu. 
Find this file in your Home directory:
.gtk_bookmarks
Click it to open and you will see all the 'places' that show up.
Simply delete the ones you do not like and close the file.
Done.

That's Nautilus Bookmarks not Places proper. What you describe can be accomplished by Bookmarks > Edit Bookmarks (Ctrl + B).

I too am looking how to edit these Places (add to them, that is) that are supposedly hard-coded. Gnome-core doesn't generate the the usual Documents, Videos, etc. folders that a normal GNOME 2 installation creates, and I'd like to remedy this.

---

