---
title: "ERROR MESSAGE, don'"
date: 2008-01-24
forum: General Help
---

### Post by Mysticpriest on 2008-01-24
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '&#8220;deb' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

-----------------

Anyone help on this error? I have no idea what it means, or how to fix it. I'm a noob at Ubuntu, please explain in detail.
Thank you.

---

### Post by lloyd_b on 2008-01-24
> **Mysticpriest said:**
> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

-----------------

Anyone help on this error? I have no idea what it means, or how to fix it. I'm a noob at Ubuntu, please explain in detail.
Thank you.

It looks like there's a typo error in that file.  Open up the file in an editor (via "sudo nano /etc/apt/sources.list" or "gksudo gedit /etc/apt/sources.list", depending on which editor you prefer), and look at line 56.  I suspect it starts as
```
"deb
```
where it should be just
```
deb
```

If that doesn't seem to be the problem, then could you please post the contents of that file?  We really need to see the contents of that file in order to diagnose this particular problem...

Lloyd B.

---

