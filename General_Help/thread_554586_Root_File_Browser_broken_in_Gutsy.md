---
title: "Root File Browser broken in Gutsy?"
date: 2007-09-19
forum: General Help
---

### Post by mark on 2007-09-19
I've been using Nautilus-root.desktop to open a file browser as root since (at least) Dapper.  The file looks like:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=File Browser (Root)
Comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;
GenericName[en_US]=

I just copy it (as root) into /usr/share/applications and the entry appears in the Applications > System Tools menu.  Invoke it, enter my password and it opens.

However, when I do this in Gutsy (latest updates as of now), nothing happens.  Any ideas  as to why?

Thanks,

Mark

---

### Post by Ankara23 on 2007-10-14
I had this same problem, so I figured the best way to test it,
 would be to enter the command directly...
~$ gksudo "nautilus --browser %U"

I got this: Couldn't find "/home/username/%U"

If I remove the %U it works, both in the console AND in the shortcut.
Hope this helps.

Ankara

---

### Post by mark on 2007-10-20
Ankara23, thanks a lot.  i figured out the same thing and changed the .desktop line to:

gksu nautilus

Without the %U, it works okay.

Mark

---

