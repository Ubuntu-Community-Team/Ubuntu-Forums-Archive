---
title: "printer setting app"
date: 2019-11-07
forum: General Help
---

### Post by jarp53 on 2019-11-07
I'm using Ubuntu 18.04.3 ; in Ubuntu Software the printer setting app shows install , and I don't have any problem with my printer, my problem is the app not showing in "show applications " I can access the printer from the search bar , but it would be nice if I can just click on the icon in my applications.

---

### Post by deadflowr on 2019-11-07
It's designed to hide it, but can be set to show.
You need to edit the .desktop file at /usr/share/applications/system-config-printer.desktop.
Should look like this

```
[Desktop Entry]
Name=Printers
GenericName=Printers
X-GNOME-FullName=Printers
Comment=Configure printers
Exec=system-config-printer
Terminal=false
Type=Application
Icon=printer
StartupNotify=true
NotShowIn=KDE;**GNOME;**
X-Ubuntu-Gettext-Domain=system-config-printer
Categories=GNOME;GTK;Settings;HardwareSettings;X-GNOME-Settings-Panel;X-Unity-Settings-Panel;System;Printing;
X-GNOME-Settings-Panel=printing
X-Unity-Settings-Panel=printing
Keywords=Printer;Queue;Print;Paper;Ink;Toner;
X-Desktop-File-Install-Version=0.24
```
you need to remove GNOME; from the NotShowIn line.
(I bolded what to remove)

Since this file, itself, can be updated if any updates come and that update will overwrite the changes, you can copy the file over to your user's home folder at
~/.local/share/applications.
Files in the user's home folder do not get overwrite by updates, so it'll stay persistent across time.
And the system always uses a user's file over the system file if it can.

Simple as
```
cp /usr/share/applications/system-config-printer.desktop ~/.local/share/applications/
```
then use gedit to edit it
```
gedit ~/.local/share/applications/system-config-printer.desktop
```

Hope it helps, or makes sense.

---

### Post by jarp53 on 2019-11-07
thanks for the quick reply and your help

---

