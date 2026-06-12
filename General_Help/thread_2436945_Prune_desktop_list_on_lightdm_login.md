---
title: "Prune desktop list on lightdm login"
date: 2020-02-15
forum: General Help
---

### Post by BobvanderPoel on 2020-02-15
My lightdm login screen is showing too many options (ubuntu, ubuntu-sofware-render, etc, etc). How can I prune the list ... there has to be file with a list of what to show somewhere!

---

### Post by deadflowr on 2020-02-15
There is no file, but entries in the login options are set as special .desktop files in either /usr/share/xsessions or /usr/share/wayland-sessions.
To hide the entries you can rename the file(s) extension to anything other than what they are.
(Or just add  something like .old or .bak to the files you want to hide. those can work too)

Note that any updates for the desktop packages related to these files might overwrite these settings,
but that should be rare, if ever.

ubuntu-sofware-render?
I only know of the cinnamon desktop environment having a software render mode as an option.
But that's just me musing...

---

### Post by BobvanderPoel on 2020-02-16
Thanks so much. Very helpful.

You did say that the desktop files are in "either /usr/share/xsessions or /usr/share/wayland-sessions". I think this is not "or" but "and" :)

Anyway, got the list pared down nicely. 

Best,

---

