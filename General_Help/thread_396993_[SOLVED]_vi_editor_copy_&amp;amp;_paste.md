---
title: "[SOLVED] vi editor copy &amp;amp; paste"
date: 2007-03-30
forum: General Help
---

### Post by Lutherian on 2007-03-30
Hi all.

I find myself using vi more and more as it's quicker than the Gnome/KDE counterparts and I like the way I can quickly type, save and exit  by just typing :w :q 

Maybe it's a limitation of my little brain, but could someone show me and example of how to

[1]
select a paragraph of text

[2]
select a column of text 

I've read the help files but I can't seem to get my head around it.
Pasting is straight forward - I just press "p"

Thanks (^_^)/`

---

### Post by DeusEx on 2007-03-30
Assuming you're running a terminal in the desktop environment:
I use select with mouse for copy and middle-button with mouse for paste.

---

### Post by girishv on 2007-03-30
Hi,

you can use ctrl-v to start a marking and then use the cursor to select. Just to get the selection into a register press 'x' (to delete) and then 'u' (to undo delete). Now the selection is registered and you can paste it using 'p' (if you have selected a column, it will be pasted as column)

You can use the same technique (instead of ctrl-v, use 'v') to select a paragraph.

Note: it has to be done in edit mode, not insert mode
         Clicking the middle button after selecting pastes  the selection into some
         applications like gedit


Girish

---

### Post by Lutherian on 2007-03-30
Thanks for the help, much appreciated. I'll try both - I'll probably start with the mouse and then ease into the keyboard mode as I get faster. From what I understand vi was designed so that the operators finger never stray away from the keyboard = faster data input.

---

