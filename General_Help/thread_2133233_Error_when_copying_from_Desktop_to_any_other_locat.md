---
title: "Error when copying from Desktop to any other location"
date: 2013-04-07
forum: General Help
---

### Post by Abvgz on 2013-04-07
I recently installed Xubuntu and there were a lot of differences I noticed between xfce and gnome. I didn't like Thunar that much (mainly because of the searching feature - even catfish doesn't posses half of the capabilities Nautilus does). So I installed Nautilus and made it the preferred File Manager from exo-preferred-applications. At first everything seemed working - the searching function, places, bookmarks etc. However, I consequently tried copying a file from the Desktop to my home folder and the following error occurred:

[ATTACH=CONFIG]241069[/ATTACH]

And after pressing Skip, another one:

[ATTACH=CONFIG]241068[/ATTACH]

I tried uninstalling thunar and xfdesktop hoping that nautilus would 'take over' the desktop but that didn't happen. Also tried with a symlink for xfdesktop -> nautilus as suggested in some thread but that didn't do the trick either.

The error occurs whenever I try copying or moving something from the desktop to another location (by Ctrl+C or Copy from the context menu). Copying and moving works from and to other locations (even from a random location to the desktop but not from it). The strangest part is that when I drag and drop a file or folder from the Desktop to the desired location it works without any errors. :confused:

This isn't such a big deal and I can certainly put up with it but I would be grateful if someone could help me resolving the problem. Thanks in advance!

---

### Post by Bashing-om on 2013-04-09
Abvgz; Hi;
Don't know, but, is this a directory/file permission issue ?
from your home directory;
```
 ls -la
``` is everything owned by you ?[INDENT=3]
just a thought
[/INDENT]

---

### Post by Abvgz on 2013-04-15
Well, most of the files and folders are owned by my user, but those whose owner is root are created from applications I run with super user, so I don't think that's the problem... Anybody else?

---

### Post by Abvgz on 2013-04-23
*bump*

---

### Post by Abvgz on 2013-04-30
bump

---

### Post by Abvgz on 2013-05-06
Anyone?

---

### Post by Merrattic on 2013-05-09
Shame you didn't give thunar more of a try, it (and its quirks) grows on you ;)

Is thunar still uninstalled ? Just an opportunity to use a different file manager other than nautilus to move files from the desktop. This would show up any permissions issues. If you don't want thunar back then try pcfm.

Can you cp or mv files from the desktop in a terminal ?

Did you install nautilus as a different user?

---

### Post by Abvgz on 2013-05-13
Well, I got used to a new gedit and rhytmbox versions due to the inability of installing older ones (I partly managed but it was such a pain in the ---). However, I just can't stand thunar and wouldn't stay with it just because of this error.

I haven't uninstalled thunar. I don't need another manager to copy/move the files from the desktop because I'm able to drag and drop them to the desired location without an error but this is time consuming and not really convenient for me. There is no error when cp/mv-ing from terminal but the following error occurs when nautilus --no-desktop is issued in terminal and a file is copied from the desktop to another location:

(nautilus:4133): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

By the way, I tried with the Live CD of Raring the other day. I just installed nautilus and the error occurred when copying from the desktop, so I don't know what the problem might be.

I don't have any other users in my system.

Also, if I open the Desktop folder in Nautilus, I'm able to copy/move any files and folders to other locations. Even if I open Thunar in one window and Nautilus in another, I'm able to copy and move anything. So I guess it's an issue with xfdesktop but I can't find a workaround or a way to force Nautilus to manage the desktop.

---

