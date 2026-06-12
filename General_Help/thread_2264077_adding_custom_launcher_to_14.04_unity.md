---
title: "adding custom launcher to 14.04 unity"
date: 2015-02-05
forum: General Help
---

### Post by decrepit on 2015-02-05
I've updated to 14.04 unity and can't figure out how to get a launcher for a Java program I use. In gnome and xfc I right clicked in a pane and added launcher.
Right clicking anywhere in unity doesn't come up with this option, so how is it done?? 
I can open from a terminal, but that's a bit messy, and beyond my wife's ability, she just wants to press a button.

---

### Post by slickymaster on 2015-02-05
You can do it by creating a simple **.desktop** file in your **~/.local/share/applications/**

With your text editor of choice**:**```
[Desktop Entry]
Name= your_application_name
Comment=
Exec=java -jar your_program.jar
Icon=/path/to/icon
Terminal=false
Type=Application
StartupNotify=true
```save this as **~/.local/share/applications/application_name.desktop**. Log off and back in.

Or you can use a GUI program to do it, which is  alacarte ("main menu") available in the software centre to make it for you. Just set the command field to the command used to run the java app.

---

### Post by decrepit on 2015-02-06
Thanks, I think both methods worked, anyway I've got 2 launchers, one on the desktop and one in the launcher panel.

---

### Post by slickymaster on 2015-02-06
You're welcome. Thanks for marking the thread as SOLVED.

---

