---
title: "executable file for &quot;Notes&quot; accessory on Xubuntu 12.04"
date: 2013-06-28
forum: General Help
---

### Post by RangerK on 2013-06-28
A want to make a keyboard shortcut for this useful accessory, but I can't seem to find the executable.  Searching for anything with the word "Notes" is also pretty difficult.  :)

Aside:  I'm only 1 week into using Linux.  Is "executable" the right terminology or is that an unwelcome intrusion from Windows parlance?

---

### Post by Impavidus on 2013-06-28
You found the "notes" accessory in the menu? (I use a different language, so it has a different name, but I think I know what you mean).

Right-click on the menu button, select "properties". Click "edit menu" and find the program you want in the list. Select it and click "properties". It will show you that the command that will start the "notes" application is **xfce4-notes**. The terminal command **whereis xfce4-notes** shows it is located in /usr/bin/xfce4-notes.

---

### Post by RangerK on 2013-06-28
Thank you.  I xfce4-notes seems to be a library file, but I found xfce4-notes.desktop in /usr/share/applications.  That does it.

EDIT:  Let me amend that.  In /usr/share/applications there's a file called xfce4-notes.desktop.  It launches notes when I click on it, but it doesn't work when I try to assign a keyboard shortcut.  It's a "desktop configuration" file.

In /usr/bin there's a "shared library" file called simply xfce4-notes.  It's not listed as an executable, so when selecting the keyboard shortcut, you must view ALL files, not just executable ones.  It works when set as a keyboard shortcut.

---

### Post by JKyleOKC on 2013-06-28
Take a look at that desktop file, using gedit, kate, leafpad, or any other text editor. It will contain a line that begins with "Exec=" and what follows the "=" will be the full path to the executable file.

---

### Post by RangerK on 2013-06-29
Thanks, JKyleOKC.

Exec=xfce4-notes
Icon=xfce4-notes-plugin
Terminal=false

I'm only a week into Ubuntu and really appreciate all the help.  I'm learning fast with help from these forums.

---

### Post by JKyleOKC on 2013-06-29
I tried running xfce4-notes here, from a terminal window, and its icon immediately appeared in the notification area of my top panel. Apparently "notes" is coded to be operated only by the mouse and running its executable only installs it into the panel. If this is indeed the case, a keyboard shortcut may not be possible -- although I'm sure that some guru would be able to create a wrapper that would accept a keyboard shortcut and then fire a faked mouse message to the notes code. Unfortunately I'm not that guru!

---

