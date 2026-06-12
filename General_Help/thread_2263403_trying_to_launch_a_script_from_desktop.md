---
title: "trying to launch a script from desktop"
date: 2015-01-31
forum: General Help
---

### Post by jgw on 2015-01-31
I am not even sure my title is correct.  Anyway, I want to create a link, on the desktop, which will execute a command.  I have found that if I open a terminal and "gedit x.sh" , for instance, enter  "#!/bin/bash" then "glsu gedit", save it, and set it to executable the file is saved to my home directory.  That file works just fine.  I then copied that file to my directory, made sure it was set to executable, double clicked it and it simply opened itself.  I tried a couple more files, doing different stuff, same results.  I also found that if I went to my file manager (pcmanfm) and clicked on the file, on the desktop, it also worked.  

By working means that it then asked me whether to execute the file, execute in a terminal, or open it.  What I want to do is simply goto the desktop, double click and get it to run.

Thank you..........

---

### Post by ajgreeny on 2015-01-31
If I understand fully what you are trying to do, I think what you need is a .desktop file on your desktop.

For example to run your gedit as root, if that's what you want, and I'm not sure about that, write a text file with content
```
[Desktop Entry]
Name=Root gedit
Comment=Root Text editor
Exec=gksu gedit
Icon=gedit
Terminal=false
Type=Application
MimeType=text/plain
Categories=GTK;Utility;TextEditor;
StartupNotify=false

```
save it as **Root-gedit** to your desktop, make it executable and it should then ask for your password and start gedit with root permissions.

---

