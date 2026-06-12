---
title: "HowTo install ms-windows program for more than one users ?"
date: 2007-04-25
forum: General Help
---

### Post by bobromeo on 2007-04-25
I do not want to install these programs withe wine several times !
{I can find nothing about this issue, so I must be missing something.}

---

### Post by Belyel on 2007-04-26
I'm not really great with wine, but it may be as simple as using 'winecfg' to tell it to look in a folder outside your home folder for the "drive_c."  The default file structure for wine is ~/.wine/drive_c/Program\ Files/ ... , so if you set it to look at, maybe /wine/drive_c/etc, and set it the same for all users, it might work.  You may also have to fiddle with the permissions of the wine directory (and subdirectories) to allow all users.

---

### Post by bobromeo on 2007-04-26
Thx, I think I'll create a separate account for doing the ms installs and then pointing c_drives of the users to the sub-dir of that user. (wine?)
I'll report back here.

---

