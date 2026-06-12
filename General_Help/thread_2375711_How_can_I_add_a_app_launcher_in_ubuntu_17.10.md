---
title: "How can I add a app launcher in ubuntu 17.10"
date: 2017-10-26
forum: General Help
---

### Post by widon1104 on 2017-10-26
How can I add a app shotcuts in ubuntu 17.10?

---

### Post by ian-weisser on 2017-10-26
Not sure what you mean.
Launching apps is pretty much most of what any OS does.

---

### Post by widon1104 on 2017-10-27
I mean add problem shortcuts

---

### Post by marcel.stancu on 2017-11-05
> **widon1104 said:**
> How can I add a app shotcuts in ubuntu 17.10?
You need to create a file named "Your_launcher.desktop" with following content:[INDENT][COLOR=#0000ff][FONT=courier new]#!/usr/bin/env xdg-open[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new][Desktop Entry][/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new]Version=1.0[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new]Terminal=false[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new]Type=Application[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new]Name=Intellij Idea[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new]Exec=/home/user_name/idea/bin/idea.sh[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new]Icon=/home/user_name/idea/bin/idea.png[/FONT][/COLOR][/INDENT]
[INDENT][COLOR=#0000ff][FONT=courier new]StartupWMClass=jetbrains-idea[/FONT][/COLOR][/INDENT]
change executable bit (with chmod +x  Your_launcher.desktop).
**Note:** value for StartupWMClass can be found using command: xprop | grep WM_CLASS and clicking inside program main window.

---

