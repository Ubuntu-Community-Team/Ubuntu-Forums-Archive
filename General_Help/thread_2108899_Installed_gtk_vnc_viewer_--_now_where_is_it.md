---
title: "Installed gtk vnc viewer -- now where is it?"
date: 2013-01-25
forum: General Help
---

### Post by Rocket J Squirrel on 2013-01-25
Lubuntu -- Used Software Center to install gtk vnc viewer. I doesn't look like it was entered into any of the start menus. But I can run it from "Run." How can I create a startup menu entry for this application?

---

### Post by mike555 on 2013-01-26
did you log out and back in? or restart?

 if it is still not in menu, use menu editing program ( like 
LXMenuEditor --    [http://lxmed.sourceforge.net/index.html](http://lxmed.sourceforge.net/index.html)  --)

---

### Post by Zvlwab on 2013-01-26
Create a file named vncviewer.desktop in ~/.local/share/applications

Add the following contents to this file:
```

[Desktop Entry]
Version=1.0
Name=GTK VNC Viewer
Comment=Add a comment here
Exec=Add the command to run it here
Icon=Add the path to an icon here
Terminal=false
Type=Application
Categories=Utility;Application;
```

The name of the file doesn't really matter actually and you can change any of the variables in this file in a way you want.
This entry should show up in the menu under Accessoires.

---

### Post by Rocket J Squirrel on 2013-01-26
Thank you, Zvlwab, it worked perfectly.

---

