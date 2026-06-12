---
title: "Emerald doesn't start ; Conflict"
date: 2008-05-15
forum: General Help
---

### Post by Jellyffs on 2008-05-15
Hello,

Since I moved to 8.04 I got this issue:

Like many I tried to change the look of my windows decoration. So first thing I did, as on edgy, feisty and gutsy, was to install Emerald. 

But, Emerald doesn't show up on start up. If I launch it in terminal, it says:

```
jelly@superdupont:~$ emerald
emerald: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
```If I add --replace, it works fine.

To make it run on start up I tried to specify it in Compiz settings manager with the option "Window decoration" by replacing /usr/bin/compiz-decorator by /usr/bin/emerald. But this had no effect at all.

It seems like emerald is in conflict with the defaut decoration manager.

My questions are:

_Where is this defaut decoration manager, and does it do the same as Emerald?
_Is Emerald depreciated on Hardy then?

Thanks a lot,

Alex.

---

### Post by Jellyffs on 2008-05-15
I actually found a way to get around this pb. Emerald was in conflict with GTK window decorator. Installing "fusion" for compiz, permits me to force the use of emerald. Now I don't even need to start fusion now.

---

