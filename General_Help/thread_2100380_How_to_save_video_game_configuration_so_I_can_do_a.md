---
title: "How to save video game configuration so I can do a fresh install of 12.10?"
date: 2013-01-01
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-01-01
I have a video game that i like to play, called 'criticalmass'. I plan on doing a fresh install of 12.10, but want to make sure I save everything necessary to restore the criticalmass game, including the configuration. The only part of the configuration I really need to preserve is the history of the top scores and the top scores themselves.

When I search the filesystem for 'criticalmass', here are the files I find:

```
/usr/games/criticalmass
/usr/share/app-install/desktop/criticalmass-data:criticalmass.desktop
/usr/share/applications/criticalmass.desktop
/usr/share/doc/criticalmass
/usr/share/doc/criticalmass-data
/usr/share/games/criticalmass
/usr/share/menu/criticalmass
/var/lib/dpkg/info/criticalmass-data.list
/var/lib/dpkg/info/criticalmass-data.md5sums
/var/lib/dpkg/info/criticalmass-data.postrm
/var/lib/dpkg/info/criticalmass-data.preinst
/var/lib/dpkg/info/criticalmass.list
/var/lib/dpkg/info/criticalmass.md5sums
/var/lib/dpkg/info/criticalmass.postinst
/var/lib/dpkg/info/criticalmass.postrm
```

I was expecting to find a criticalmass entry in my home folder though...since each user has their own set of parameters.

How do I save the currently existing criticalmass configuration so I can restore it once I have 12.10 installed?

TY.

Art

---

### Post by zero2xiii on 2013-01-01
Hay,

Just out of curiosity did you include hidden files and folders?

Most programs (and games) store their config files and so forth in the home folder in a hidden directory starting wit a full stop (.)..

Try also looking for the developers name instead of the game name? Or maybe an older version name (pidgin comes to mind which calls it directories lib-purple.. well on my computer anyway)

otherwise. What does the man page of the game say? usually it contains a directory list.

Cherz

---

### Post by goodbye-windows(tm) on 2013-01-01
Thanks Cherz,

My search function finds hidden files by default, so there isn't a hidden file that contains 'criticalmass'.

However, the author refers to the game a 'criticalmass (aka critter)'. Searches for 'critter' gave me answer I needed, many thanks for joggin my memory!!!! Also found 'man critter' entry, although there was no manpage for 'criticalmass'.

Again, ty.

Art

---

