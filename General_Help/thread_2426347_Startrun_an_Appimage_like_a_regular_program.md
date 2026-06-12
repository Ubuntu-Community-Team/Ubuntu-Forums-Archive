---
title: "Start/run an Appimage like a regular program"
date: 2019-09-07
forum: General Help
---

### Post by crip720 on 2019-09-07
I downloaded ultimaker cura as an appimage and it is working well.  My only problem is that I don't know how to set it to work like a regular program or if it can be done, as in one chick and program runs.  I am so far have to open files, open downloads, click on ultimaker and click 'run'.  Does not seem to want to to run from dash.  I am using ubuntu 19.04 with unity desktop.

---

### Post by Dennis N on 2019-09-07
I place all my appimages in ~/appimages. Some of them create their own .desktop file with a menu launcher and icon on first run (example: etcher). Others you have to manually create a .desktop file in ~/.local/share/applications. Ubuntu will pick up these entries and make a menu entry, and they also appear in overview screen. If no icon is found, you can probably find an .svg image using google image search.

---

### Post by ajgreeny on 2019-09-07
Having downloaded the appimage you must now give it execute permissions, so assuming it's in your Downloads folder run command chmod +x Downloads/name-of-appimage.Appimage

You can then create a launcher for it.  This is a text file with content
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Ultimaker
Comment=*description of application*
Exec=/home/*username*/Downloads/name-of-appimage.AppImage
Icon=*path to any icon you want to use*
Categories=GTK;*Multimedia;Qt;Audio;Sequencer;Midi;AudioVideoEditing;Music;AudioVideo;* # This an example; I have no idea what that application is.
Path=
Terminal=false
StartupNotify=false

```
Save this file as Ultimaker.desktop, make it excutable and put it in the hidden ~/.local/share/applications/ folder.  I think it should then show in the menu/applications listed in your gnome desktop.

---

### Post by crip720 on 2019-09-07
Thank you for your replies, for ajgreeny, ultimaker cura is a program for 3d printers, think it changes a downloaded 'stl' file and slices it to a gcode file for printer to print from. New to this and just having fun with it for now, not quite sure what category it fits.  I am using the unity desktop if it makes a difference.

---

### Post by ajgreeny on 2019-09-07
> **crip720 said:**
> Thank you for your replies, for ajgreeny, ultimaker cura is a program for 3d printers, think it changes a downloaded 'stl' file and slices it to a gcode file for printer to print from. New to this and just having fun with it for now, not quite sure what category it fits.  I am using the unity desktop if it makes a difference.
As this launcher relates to printing it makes sense to use ```
Categories=GNOME;GTK;Settings;HardwareSettings;X-GNOME-Settings-Panel;X-Unity-Settings-Panel;System;Printing;
```
in that .desktop launcher.

---

