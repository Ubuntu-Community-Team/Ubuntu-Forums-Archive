---
title: "Konqueror points to deleted folder"
date: 2015-01-01
forum: General Help
---

### Post by paul187 on 2015-01-01
Hello, I wanted to try some different file managers, and so far I like Konqueror.  Problem is, when I run it from the launcher, Konqueror points to a sub-folder in my home directory.  Is there a way to change this, so that Konqueror loads my home directory instead? I've waded through all of the settings in Konqueror, and Googling has not provided a solution.  I've tried moving the folder, and Konqueror still loads the same (now missing) folder.

Thanks.

---

### Post by ajgreeny on 2015-01-01
How do you start konqueror, with a launcher from the desktop or menu?

That will probably be a **konqueror.desktop** file, which is a plain text file that you can edit with kate or gedit, or whatever text editor you use.  Depending on where the .desktop file is, you may need to do it as root.

Look for the line that is **Exec=konqueror %u** or similar and change it to **Exec=konqueror /home/*username*** and it should then open in your home folder.  There may also be a line with **Path=path/to/folder** which you may need to edit, or even remove, as it is not normally necessary.

It's very odd that it doesn't do so by default, but that may be something to do with using a qt/kde application in what is I assume not a full kde DE system, or having moved the menu item or launcher icon from somewhere else.

---

