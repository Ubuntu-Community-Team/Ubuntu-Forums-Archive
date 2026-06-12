---
title: "Share pidgin profile over dual boot?"
date: 2007-06-29
forum: General Help
---

### Post by allspiritseve on 2007-06-29
I am wondering if it is possible to allow pidgin to use the same profile whether on windows xp or kubuntu. I can't find anything in the settings for profile location, but maybe there are some files somewhere I could edit?

Thanks,

Cory

---

### Post by collinjc on 2008-01-21
The only way I have been able to find to do this is to replace the .purple directory with a link to the windows .purple directory under /windows/Documents and Settings/username/Application Data/.purple . Once the link is renamed to .purple, it seems to work okay.

---

### Post by SentientFluid on 2008-05-21
I've found the easiest way is to make sure your Windows partition is mounted (with read/write access), then create a custom launcher with something like this in the command field:

```
pidgin -c /path/to/.purple/on/windows/mount
```

For me it looks like this:

```
pidgin -c /mnt/XP/Documents\ and\ Settings/windowsusername/Application\ Data/.purple
```

---

