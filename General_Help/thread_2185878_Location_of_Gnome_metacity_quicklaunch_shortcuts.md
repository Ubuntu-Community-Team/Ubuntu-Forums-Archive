---
title: "Location of Gnome metacity quicklaunch shortcuts?"
date: 2013-11-04
forum: General Help
---

### Post by helloworld1215 on 2013-11-04
What is the directory or configuration registry that .desktop files are copied to when a .desktop  file is dragged to the Gnome Clasic quicklaunch bar? I would like to be  able to modify them directly

---

### Post by stinkeye on 2013-11-04
Look in **~/.local/share/applications**. 
If the desktop file is not there, you need to copy it from 
**/usr/share/applications ** to **~/.local/share/applications**.
Don't use sudo , just copy as a normal user.

Then edit via terminal...
```
gedit ~/.local/share/applications/[COLOR="#696969"]xxxx.desktop[/COLOR]
```
or 
goto **~/.local/share/applications** in the file browser and drag and drop **~/.local/share/applications/[COLOR="#696969"]xxxx.desktop[/COLOR]** into a gedit window.

.desktop files in **~/.local/share/applications** override those of same name in **/usr/share/applications**
To revert back just remove the edited [COLOR="#696969"]xxxx[/COLOR].desktop from **~/.local/share/applications**

If the shortcut is already on the panel before editing the new .desktop file,
you will probably need to remove and re-add or log out/in.

---

### Post by helloworld1215 on 2013-11-05
Neither of those places seem to contain the .desktop files associated with the Quicklaunch bar of the Gnome Metacity I don't think (ie I've checked and they're not there but anything is possible I suppose). 

/usr/share/application contains .desktop files associated with the applications and places menu and memetype associations as specified by the defaults.list. ~/.local/share/applications generally contain desktop files associated with memetype associations as well.

I have actually file name and file content searched the home directory for said .desktop files and have not been able to locate them. I have search gconf as well.

---

### Post by helloworld1215 on 2013-11-05
I have found the answers!

The configuration is at dconf accessed by dconf-editor: org.gnome.gnome-panel.layout.

The objects at: org.gnome.gnome-panel.layout.objects

When dragged to the gnome-panel, the original dragged desktop is specified in the configuration. 

Execute: killall gnome-panel to propagate changes to said .desktop files.

---

