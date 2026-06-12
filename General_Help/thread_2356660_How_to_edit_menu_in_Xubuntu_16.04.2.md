---
title: "How to edit menu in Xubuntu 16.04.2"
date: 2017-03-25
forum: General Help
---

### Post by lynx6 on 2017-03-25
Hello,


How to put the *Gnome Software Center *in the *System* category in the menu Xubuntu 16.04.2.
I already entered the menu editor but I could not.
How do you do it?
Thank you.

---

### Post by Dennis N on 2017-03-25
No need to use menu editor. If you want it to display under System, do the following:

With a text editor, edit the file [B]/usr/share/applications/gnome-software-local-file.desktop
[/B]
Add the # where shown:

```
[Desktop Entry]
Name=Software Install
Comment=Install selected software on the system
Categories=System;
Exec=gnome-software --local-filename=%f
Terminal=false
Type=Application
Icon=system-software-install
StartupNotify=true
[COLOR="#FF0000"]#NoDisplay=true[/COLOR]
MimeType=application/x-rpm;application/x-redhat-package-manager;application/x-deb;application/x-app-package;application/vnd.ms-cab-compressed;application/vnd.xdgapp;x-scheme-handler/apt;application/vnd.snap;
X-Ubuntu-Gettext-Domain=gnome-software

```
Save, log out, then log in and it should display under System as "Software Install". 

Note: I get a little error box when I start it, but close the box and the main program will start. Beyond that, I have not used it myself!

---

### Post by lynx6 on 2017-03-25
Hello *Dennis. *Thank you very much for your time and help.
I did the procedures and not resolved, *Gnome Software Center* remains in Favorites, but no problem.

---

### Post by Dennis N on 2017-03-25
Let's try another way and use the menu editor. I was able to get a launcher in Settings that way as well. The screenshot attached shows how the information was filled out.

Briefly - right click on menu icon on panel, select "Edit Applications". Highlight "System" category. Click "+" on top bar and select "add launcher". Click "New Launcher" on right and replace it with program name. Click the question mark and replace by an appropriate icon. Fill in the command to start it (see attached screenshot). Click "Save" Button on top bar. Done. It then shows with title "Gnome Software" under "System" category. Also, no error message on start, which is nice.

Added comment: The .desktop file for the launcher is saved in ~/.local/share/applications as menulibre-gnome-software.desktop. It dosn't use the one in /usr/share/applications.

---

### Post by lynx6 on 2017-03-29
Hello Dennis N,

In this second tip I managed to put *Gnome Software Center* in the category [I]System.
[/I]It was necessary to follow the procedures that you indicated to work right .
Thank you very much for your attention.

---

### Post by mörgæs on 2017-03-29
Thanks for attempting to mark the thread solved but it's better to use Thread Tools.

---

### Post by lynx6 on 2017-03-29
Thank you. All ok, I edited the post.

---

