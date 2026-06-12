---
title: "I'll grant you that..."
date: 2008-04-26
forum: General Help
---

### Post by dawhistler on 2008-04-26
How can I log in as root to a gui?   I just did this last week but have misplaced my instructions.
I am trying to access a usb hard drive that suddenly kicked me out...

---

### Post by pbpersson on 2008-04-26
This is just a guess on my part, but I would go into recovery mode (hit ESC when GRUB loads) and I think it will give you an option there.

If you all get is the text only mode then once you are in there type "startx" and that should get you a GUI

---

### Post by dawhistler on 2008-04-26
To be more specific...

I upgraded to Gutsy from 7.10

When I did this my usb drive stayed mountable but became unreadable.

I get the message that it is ext-3 but has nosuid nodev relatime data=ordered

Also   The permissions of "disk-18" could not be determined.


I guess I need to assign permissions but dont know how.

---

### Post by p_quarles on 2008-04-26
Thread closed. Sorry, but graphical root logins are not supported here. Read the following for more information:
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

You can run individual graphical apps with root permissions very easily. For instance:
```
gksu gedit
```
will open the default text editor with root permissions. You can even make launchers that include the gksu command to make this easier. This is the only recommended way of using graphical apps with root permissions.

---

