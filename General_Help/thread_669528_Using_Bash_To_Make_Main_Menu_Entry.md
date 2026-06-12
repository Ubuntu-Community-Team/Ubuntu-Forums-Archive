---
title: "Using Bash To Make Main Menu Entry"
date: 2008-01-16
forum: General Help
---

### Post by Greasyfingers on 2008-01-16
Is there a way to make a main menu entry from a bash script? I've managed to turn up an example of a script that puts a desktop launcher on the desktop, but can't find anything that shows how to put an entry into the menu (the one which you open from the panel).

Anybody help?

---

### Post by fwojciec on 2008-01-17
If I understand you correctly...

Have a look in /usr/share/applications.  You'll find a bunch of *.desktop files in there; there should be one for each entry in the menu.  Making things show up in the menu means creating a *.desktop file for a given application and placing it in /usr/share/applications.  I'm not sure how you'd do it using a bash script, you'd have to be more specific about what it is that you're trying to achieve...  The easiest thing to do is to just create the file manually or use something like alacarte for gnome to create it using a GUI.

---

### Post by Greasyfingers on 2008-01-17
Thanks, fwojciec, that's given me half a clue, anyway. I can make a menu entry now, by doing pretty much the same as I discovered for the desktop entry, but instead of putting it in /home/user/Desktop/ it goes in /usr/share/applications/ like this:```
#!/bin/bash

echo "
[Desktop Entry]
Encoding=UTF-8
Type=Application
Terminal=false
Icon=gnome-panel-launcher
Exec=/path/to/application
Name=AppName" >> /usr/share/applications/appname.desktop
``` But I can't seem to control which section of the menu it appears in (clearly, there are more fields that I need to find out about), and I'm a little surprised that root access is needed for this when I can do the same thing with Alacarte as user.

I'm really only trying to do this to gain knowledge and understanding of how things work - I've just written my first real bash script, and want to find out what sort of things it's capable of.

---

### Post by fwojciec on 2008-01-17
Have a look at some more *.desktop files and look at Categories tag -- this is what determines the place in the menu.

As for why alacarte can do it without root access, I don't know -- I don't use gnome so I've no way of checking.  My guess is that there is another, user specific "applications" directory with *.desktop files somewhere in you /home dir -- try checking in ~/.config for example, maybe you'll find it.

EDIT: Found it, it's ~/.local/share/applications.  Whatever you put in there will only show up for the particular user, of course.

---

### Post by Greasyfingers on 2008-01-17
Excellent.

Thanks again, fwojciec.

---

