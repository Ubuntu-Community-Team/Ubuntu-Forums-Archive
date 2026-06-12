---
title: "Can not open Adobe Reader from Desktop"
date: 2006-11-08
forum: General Help
---

### Post by koala114 on 2006-11-08
I've installed Adobe Reader 7.0 on Ubuntu 6.06, but I can't start it if I click from main menu or from the shortcut in the desktop.
I issue the command 'acroread' from terminal, however, it will works well. 
And Openoffice also seemed to be hang on the screen with splash if I click from main menu, nothing happened. If I issue /usr/lib/openoffice/soffice, it also works well.
:confused:

---

### Post by ajgreeny on 2006-11-08
Not sure why it should be, but it sounds as if your launchers in the main menu are pointing to the wrong binary file.  Right click on the menu entry and see where the launchers point and what the command is; if it is different to what you use in the terminal, try changing to that and see if the menu then works.

---

