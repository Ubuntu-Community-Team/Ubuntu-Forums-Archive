---
title: "Desktop Launcher Icons/Files"
date: 2013-02-16
forum: General Help
---

### Post by Quarkrad on 2013-02-16
I have been creating desktop launchers both within the Unity launcher and on the actual desktop.  I do this be creating a .desktop file in /usr/share/applications in the form of:

[Desktop Entry]
Version=3
Type=Application
Terminal=false
StartupNotify=true
Icon=suspendbutton
Name=test
Comment=Programming IDE
Exec=abcd
Categories=Application;Development;

This is all great but when the file/icon is dragged onto the desktop the name is visible beneath the icon.  Is it possible to create a launcher that has no name?   The same issue applies if you create a launcher using  **gnome-desktop-item-edit ~/Desktop/ --create-new**  it looks to me that you have to have a name.  Note.  When used on the actual desktop I'm using gnome classic.

---

### Post by Bufeu on 2013-02-16
No. You can't.
[http://askubuntu.com/questions/23570/how-can-i-hide-the-text-under-the-desktop-icons](http://askubuntu.com/questions/23570/how-can-i-hide-the-text-under-the-desktop-icons)
**NOTE: That will affect all your desktop icons!**

---

