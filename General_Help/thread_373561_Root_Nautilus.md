---
title: "Root Nautilus"
date: 2007-03-01
forum: General Help
---

### Post by Irony on 2007-03-01
If I do;

[PHP]gksudo nautilus[/PHP]

I have root nautilus and from here I can click on text files to open as root.

But if instead I right click on a folder and choose;

[PHP]Scripts > open_as_root[/PHP]

I'm again in root nautilus but  when I click on text files to open as root nothing happens - it worked in Dapper but not now in edgy.

This is my scripts file;
[PHP]
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gksudo "gnome-open $uri" &
done[/PHP]

---

### Post by CocoAUS on 2007-03-01
Interesting.  I hadn't noticed this (I tend to use the command line to edit files as root), but I've tried it, and I'm having the same problem.

---

### Post by Irony on 2007-03-01
It must be using a different path because I find that if I do gksudo nautilus I have to type the password but if I then close it and then do open_as_root I have to do the password again.

Normally Ubuntu remembers (for 15 mins) passwords for things opened graphically or terminally - but it treats these as though they are entirely separate like one graphical, one terminal and one open_as_root.

In Dapper it was one graphical/open_as_root and one terminal.

---

