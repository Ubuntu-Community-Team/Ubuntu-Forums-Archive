---
title: "I cant boot into Ubuntu."
date: 2008-06-18
forum: General Help
---

### Post by Kyle_vdk on 2008-06-18
I just reinstalled windows, did not touch the Ubuntu partition at all, but now the Grub thing doesnt work, just boots into Windows, doesn't show any Grub menu.

---

### Post by nikgare on 2008-06-18
See this thread:

[http://ubuntuforums.org/showthread.php?t=829696&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=829696&highlight=reinstall+grub)

Nik

---

### Post by Kyle_vdk on 2008-06-18
I got an error on the setup (hd0) part... said like it wasn't recognized

---

### Post by nikgare on 2008-06-19
So you're half way there - you have grub installed.
You just have to give it the right information.
When you boot the computer you will need to hit escape to get top the grub menu dialogue.  Here you will need to edit the default option so that it points to the correct disk - hd0 is incorrect.

---

