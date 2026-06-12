---
title: "[SOLVED] Windows are opening too big"
date: 2008-02-21
forum: General Help
---

### Post by dstein on 2008-02-21
Hello. Sometimes when I load a program, the window size is too large for my desktop. I must then right click somewhere, then click resize, and then fit it on my screen. It happens mostly with PDF files opening in Evince Document Viewer. Any ideas why this is happening and how to fix it? I would like my programs to open in a window that fits on my desktop. Thanks.

---

### Post by goulo on 2008-02-21
This happens to me too opening PDF files, and also with, e.g., the print popup in Gimp and various other specific situations.  It is as if the program is not aware that there is a task bar at the bottom of the screen, and the opened window is too tall and the bottom of it goes behind the task bar.  Quite consistently annoying.

---

### Post by chiefmanyrabbitguteat on 2008-03-11
This worked for me:

Open up your Home folder and show hidden files (ctrl+h)

navigate to ~yourusername/.gnome2/evince

Right-click on the file "ev-metadata.xml" and select "open with Text Editor."  This file apparently tells Gnome how to handle Evince windows

Erase everything in the file, save it and close it.

Right click on the file, select "Properties"
Under the permissions tab, change everything to "Read Only"

This prevents the file from being overwritten.


Hope this helps

---

