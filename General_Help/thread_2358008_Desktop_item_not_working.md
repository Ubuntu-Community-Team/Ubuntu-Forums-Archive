---
title: "Desktop item not working"
date: 2017-04-08
forum: General Help
---

### Post by raleigh3 on 2017-04-08
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=
Comment=
Keywords=
Exec=echo gggg | sudo -S thunar
Icon=/home/andy/Icons/
Categories=
Terminal=false
StartupNotify=true
Name[en_US]=

```

Exec statement works in a script, but I can not change the icon of a script on the desktop.

---

### Post by deadflowr on 2017-04-08
sudo requires a terminal.
use gksu (needs to be installed, probably; *sudo apt install gksu*)

---

### Post by raleigh3 on 2017-04-08
> **deadflowr said:**
> sudo requires a terminal.
use gksu (needs to be installed, probably; *sudo apt install gksu*)

Actually sudo does not need a terminal.

I put scripts on my desktop using sudo.
They work fine, but you can not change their icons. :-(

---

### Post by deadflowr on 2017-04-09
Let me rephrase that:
Don't use sudo to open graphical applications.
For shell commands and terminal-based applications, it is fine.
But it can have unwanted consequences when ran to open a graphical app.

---

