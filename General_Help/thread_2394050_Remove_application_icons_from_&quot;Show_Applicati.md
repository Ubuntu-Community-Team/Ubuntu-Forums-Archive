---
title: "Remove application icons from &quot;Show Applications&quot; menu"
date: 2018-06-11
forum: General Help
---

### Post by rgoodelljr on 2018-06-11
I am currently running Ubuntu 18.04 gnome and I am having an issue. For some reason I decided it would be a great idea to remove wine without uninstalling all of its software in itself. I have a couple things in the "Show Applications" menu that I do not wish to see there. These include: Python 2.6 packages for wine, and  Winrar. None of these packages seem to be usable (as expected) so I am wondering how to remove these icons from within the menu.

---

### Post by deadflowr on 2018-06-11
First look to see if you still have a hidden .wine folder ~/.wine
And then remove it. If you don
t need it then you don't need it right?

Second look in your local share folder ~/.local/share/applications
and see if you have any wine related desktop files in there. Or files with names related to the wine apps.
And remove those.

Then see what shows and what doesn't.

[the .wine and .local folder are hidden by default so to access them in the Files program press ctrl + H.
That usually works; I think alternatively you can access the show hidden folders/files in the hamburger-like icon in the top right side of Files title bar]

Sidenote, by design when removing applications the system does not remove any associated files from any users home folder.
This makes it easy to restore settings if the program itself needed to be cleaned (removed and reinstalled)
It also keeps any user data save, like Documents or Game files or whatever you can think of that you'd not want purged because a program was removed.
So in these cases you need to remove the files yourself, which is okay as you will have the perfect rights to remove anything in your own home folder. So  no need for sudo to do that.

Hope it helps
or makes sense

---

### Post by markrazorx on 2018-10-31
Is there a way to see the hidden files in 18.04 through the GUI?

---

### Post by vanadium on 2018-11-01
To prevent certain programs from showing up in your application overview, find its desktop file and add a line "OnlyShowIn=".

If you do not have root permissions, or want to make sure that a future update does not undo your change, then copy the desktop file to your privant ~/.local/share/application folder, and edit the copy. A .desktop file in ~/.local/share/application has priority over a .desktop file in the system wide /usr/share/applications folder.

---

### Post by l33ch on 2018-11-04
Menu Editor (menulibre) is a great program to edit the App Menu. Add/Remove/Edit Launchers, etc.

```
sudo apt-get install menulibre
```

There will be a menu item called Menu Editor listed under Settings Manager you can click on to edit the app menu.  I used this to add icon(s) for a couple web browsers under Internet.Works great.

---

