---
title: "Computer and Terminal icons off screen after restart"
date: 2015-09-09
forum: General Help
---

### Post by BarryD9545 on 2015-09-09
I just upgraded to 15.04 and this issue started.

At each restart, the icons for Computer and Terminal are missing.  They are still in the desktop folder, and readily drag into place from that folder back onto the desktop every time.

Here are the files:
[TABLE="class: grid, width: 500"]
[TR]
[TD]Terminal[/TD]
[TD]Computer[/TD]
[/TR]
[TR]
[TD]#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Terminal
Comment=Use the command line
Keywords=shell;prompt;command;commandline;
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.14.2
Categories=GNOME;GTK;System;TerminalEmulator;
StartupNotify=true
X-GNOME-SingleWindow=false
OnlyShowIn=GNOME;Unity;
Actions=New
X-Ubuntu-Gettext-Domain=gnome-terminal


[Desktop Action New]
Name=New Terminal
Exec=gnome-terminal
#OnlyShowIn=GNOME;Unity;[/TD]
[TD][Desktop Entry]
Name=Computer
Comment=Access and organize files
Keywords=folder;manager;explore;disk;filesystem;
Exec=nautilus --new-window /
Icon=system
Terminal=false
Type=Application
StartupNotify=true
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Utility;
MimeType=inode/directory;application/x-gnome-saved-search;
Actions=Window;


[Desktop Action New]
Name=New Terminal
Exec=gnome-terminal
#OnlyShowIn=GNOME;Unity;[/TD]
[/TR]
[/TABLE]

Thanks for the help.

---

### Post by Bucky Ball on 2015-09-09
*Thread moved to **General Help**.*

Might have more luck here.

---

### Post by BarryD9545 on 2015-09-21
Bump

---

### Post by BarryD9545 on 2015-10-01
I came up with these that leave the icons on my Gnome Fallback screens

[TABLE="width: 500"]
[TR]
[TD]Terminal.desktop[/TD]
[TD]Computer.desktop[/TD]
[/TR]
[TR]
[TD][Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gnome-terminal
Name=qTerminal
Icon=terminal[/TD]
[TD][Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=nautilus computer:///
Name=Computer
Icon=computer[/TD]
[/TR]
[/TABLE]

And then run in terminal:
```
$ sudo [COLOR=#111111][FONT=Consolas]chmod +x $HOME/Desktop/Computer.desktop[/FONT][/COLOR]
```[COLOR=#111111][FONT=Consolas]
and
[/FONT][/COLOR]```
$ sudo [COLOR=#111111][FONT=Consolas]chmod +x $HOME/Desktop/Terminal.desktop[/FONT][/COLOR]
```
Happy Ubunting!

---

