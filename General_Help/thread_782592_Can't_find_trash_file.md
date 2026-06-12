---
title: "Can't find trash file"
date: 2008-05-05
forum: General Help
---

### Post by piercleo on 2008-05-05
I have a file in my trash which I need to delete using sudo in command line. The problem is I can't find my trash file. It is not in my home/username/.trash where I thought it would be.

For info, I have a clean Hardy install.

Any idea ?

Thx

PierC

---

### Post by sdennie on 2008-05-05
The trash should be located at ~/.local/share/Trash.  However, there are two directories there (files and info) so, if you move a file out of the files directory, you may want to remove the corresponding .trashinfo file from the info directory as well.

---

### Post by Benjamin_Vedder on 2008-05-05
i think the files are located in /home/username/.local/share/Trash/files. Type sudo nautilus in the terminal to open the file browser as root. That folder is hidden, so hit ctrl + h in nautilus to see it.

---

### Post by piercleo on 2008-05-05
Thank you very much, was able to delete my file. Maybe the info of the trash location could be added to the help menu.

PierC

---

### Post by piercleo on 2008-05-05
Sorry for the newbie question but how to I write Solved in the title ?

---

