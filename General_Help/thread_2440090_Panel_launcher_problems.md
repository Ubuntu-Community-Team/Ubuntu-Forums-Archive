---
title: "Panel launcher problems"
date: 2020-04-05
forum: General Help
---

### Post by dkolars on 2020-04-05
18.04. 
Add launcher to panel... add program...  Launcher is not editable...  cannot load icon for program (Avidemux 2.7.4)...  Where did the "Edit" go for the launchers?  When upgrading, have to delete program from launcher and add new instead of just changing path.  NO option to add/change the icon???  Grrr

---

### Post by owbizi on 2020-04-06
Programs are added from desktop launchers, such as the ones located in **~/.local/share/applications** (user-wide) or **/usr/share/applications** (system-wide).

Here is an example for a custom launcher I made to add Sublime Text to the list of applications installed:

> 
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Sublime Text
GenericName=Code editor
Comment=Edit code with Sublime Text
Exec=subl %F
Icon=sublime-text
Terminal=false
Type=Application
MimeType=text/plain;
Categories=Utility;TextEditor;Development;IDE;


---

