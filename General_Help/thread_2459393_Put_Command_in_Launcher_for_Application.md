---
title: "Put Command in Launcher for Application"
date: 2021-03-17
forum: General Help
---

### Post by SkyQuake on 2021-03-17
Hello,

How do I put a command into a Launcher icon from the desktop in Ubuntu 20.04? In Debian, it is easy. It is under the Permissions menu. 

Specifically, instead of directly launching a program, I need to qualify that is has to use an earlier version of MESA when launching after double-clicking the desktop icon.

Here is the command that needs to be executed from the icon:

env MESA_GL_VERSION_OVERRIDE=3.3 obs

From Terminal, this launches OBS Studio properly.

Thank You for your help.

---

### Post by daniewicz on 2021-03-17
You can put an icon on the desktop to launch some code, but I don't believe you can do this from the dock.

---

### Post by Holger_Gehrke on 2021-03-18
Is the 'xubuntu' tag in the heading an error ? In XUbuntu you can just  right click on the desktop, select 'Create New Launcher' (or words to  that effect, I'm retranslating from the German) and get a form you just  fill in. You can then move the new .desktop-file from the desktop  directory into ~/.local/share/applications/ if you want to have the launcher in the  menu. You can also right click on an application in the menu or a starter on the desktop, select 'Edit application' and change the 'Command' field.

Mainline Ubuntu uses a relatively new version of the Gnome desktop, one in which the code to draw the desktop was removed from the file manager which used to do that. The problem was that this code was getting somewhat baroque and nobody wanted to work on it, so the plan as far as I know is to write a new separate program for drawing the desktop and any icons on it and reacting to manipulation of these icons. This is not done yet and the only way to get icons on the desktop currently is to use a Gnome Shell extension.

Launchers are simple text files with the extension '.desktop'. The structure of these files is documented [here]("https://specifications.freedesktop.org/desktop-entry-spec/latest/"). The menus in the various desktops are created from desktop files that are in the directory '/usr/share/applications/' for menu items that are available to all users and in '~/.local/share/applications/' for user specific program launchers.

Holger

---

### Post by daniewicz on 2021-03-18
I have a .desktop file I have created that places an icon on my desktop when placed in my desktop folder. if I copy this file to .local/share/applications/ the icon does not appear on the dock. 
Ubuntu 20.04.2

---

