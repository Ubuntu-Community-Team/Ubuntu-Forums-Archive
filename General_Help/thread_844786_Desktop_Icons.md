---
title: "Desktop Icons"
date: 2008-06-29
forum: General Help
---

### Post by McTek on 2008-06-29
I would like to have my files Icon on the Desktop. In 7.10 I was able to drag and drop the icon, but 8.04 does not allow that. Is there another way to do this. I have all my other partitions On the Desktop through fstab editing but can't get my files Icon to work.

---

### Post by theshadowwithanmp5n on 2008-06-29
use the mv command in the terminal to move it to Desktop.
an example would be

mv home/mctek/pictures /home/mctek/Desktop

---

### Post by McTek on 2008-06-30
That does not work for My Comupter folder.

---

### Post by temaki on 2008-06-30
I think you are referring to Computer? I did this recently by doing the following:

alt+F2 -> gconf-editor ->apps->nautilus->desktop->computer_icon_visible checked.

---

