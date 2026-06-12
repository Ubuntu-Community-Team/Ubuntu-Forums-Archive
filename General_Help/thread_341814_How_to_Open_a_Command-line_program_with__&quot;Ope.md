---
title: "How to Open a Command-line program with  &quot;Open with another application&quot;"
date: 2007-01-19
forum: General Help
---

### Post by LeviNelson on 2007-01-19
How to Open a Command-line program with  "Open with another application".

Hi, I am trying to use a command-line program (par2) without having to actually use the command line. The program is located at /usr/bin/par2repair. I am trying to be able to double click or right click and be able to select it to run the file I am selecting. So far I have tried to use the "custom command" '/usr/bin/par2repair' under the "open with other application " window, but that doesn't seem to be working. When I click on it, it does nothing. At least I can't see it doing anything...

Any help would be greatly appreciated. 
Thanks, Levi.]

---

### Post by jpeddicord on 2007-01-19
Try doing it this way:
Right-click on Applications and select Edit Menus. Add the command as a new menu item under System Tools or whichever category you see fit. Give it a name and icon if you want. Save it, and close the editor. You should now be able to launch it from the Applications menu as well as from the Open With menu.

Another solution is use `par2repair %u` as the command to be able to open files with it.

---

### Post by LeviNelson on 2007-01-19
Perfect. The first solution of yours worked wonderfully. Thanks for the quick response and spot on answer!

Levi

---

