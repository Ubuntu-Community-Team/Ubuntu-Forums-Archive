---
title: "[SOLVED] please help with ubuntu studio 8.04 graphics settings"
date: 2008-05-27
forum: General Help
---

### Post by hurtstotalktoyou on 2008-05-27
Hi, all.

When I installed the plain-jane ubuntu 8.04 hardy heron, my 17" CRT display was not properly detected (effectively limiting me to 800x600 resolution). I had to go into the "Screens and Graphics" tool and tell it what settings to use. Unfortunately, the "Screens and Graphics" tool is not set up by default in 8.04, so I had to go to System > Preferences > Main Menu, then click on "Other" in the "Applications" menu, and then check the box next to "Screens and Graphics." This worked fine.

Today I installed ubuntu studio 8.04. As expected, it did not properly detect my 17" CRT display. So I went to System > Preferences > Main Menu, as before, to check the "Screens and Graphics" box. Much to my surprise, however, that box doesn't exist! In fact, the "Other" list is completely empty.

So, what do I do now? How do I get the "Screens and Graphics" tool to show up? Is it even installed? If not, can I perhaps find it in synaptic? If it is installed, can I run it from terminal using a package name? If so, what is the package name? If it's not available, is there some other way to tell ubuntu studio what settings to use with my 17" CRT display?

Any help would be much appreciated!

---

### Post by danwood76 on 2008-05-27
The name of that app is displayconfig-gtk
So to run it press alt+F2 and run:
```

gksu displayconfig-gtk

```
It should be installed as it is part of the GNOME package I think

---

### Post by hurtstotalktoyou on 2008-05-27
> **danwood76 said:**
> The name of that app is displayconfig-gtk
So to run it press alt+F2 and run:
```

gksu displayconfig-gtk

```
It should be installed as it is part of the GNOME package I think

That worked perfectly!  Thanks a million!

---

