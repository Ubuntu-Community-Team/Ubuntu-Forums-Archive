---
title: "[SOLVED] Command to create terminal profile"
date: 2007-10-02
forum: General Help
---

### Post by dje on 2007-10-02
What command can i use to create a terminal profile or what do i need to put into a certain file to create/configure the new profile. I use gnome-terminal. Thanks in advance.

---

### Post by dje on 2007-10-02
anyone? perhaps you dont understand what I mean??

---

### Post by p_quarles on 2007-10-02
The easiest way is to click on the toolbar and find the "edit profile" option (not using Gnome right now, and I can't remember which menu it's under). That will allow you to customize the appearance of the terminal and so forth.

If you *really* want to edit it manually, open up the .profile file in your home directory. 

Does that answer your question?

---

### Post by dje on 2007-10-03
Thanks but i already know how to do that with the edit profile button!
And the .profile file isn't really what i wanted either
Thanks for the help though :)

Just to clarify, what i meant is a file like this (for a menu item):
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=System Backup
Comment=Backup your entire system
Exec=gnome-terminal --window-with-profile=systembackup
Icon=/usr/share/pixmaps/gfloppy.xpm
Terminal=false
Type=Application
Categories=Application;System Tools;
GenericName[en_GB]=
```
but for a terminal profile, can this be done?

---

### Post by dje on 2007-10-03
I found what i was looking for in /home/YOUR USER/.gconf/apps/gnome-terminal/profiles

---

