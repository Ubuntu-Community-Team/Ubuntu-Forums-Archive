---
title: "removing firefox - also removes other packages???"
date: 2008-06-15
forum: General Help
---

### Post by bluepowder7 on 2008-06-15
so i'm transitioning away from firefox and into opera.  about to remove firefox64 and it says it needs to also remove a bunch of other packages (see image below).

should i worry about it removing things like "gnome-user-guide" and "ubuntu-desktop" and "ubuntu-docs"???  those sound like they're pretty freakin' vital to having a working GUI.

i plan on installing and having ONLY the firefox32 browser, since that seems to be the best way of having flash work - and i'd only be using it for youtube and other similar sites.  keeping opera for the REAL browsing. :popcorn:

[IMG]http://i106.photobucket.com/albums/m244/GregR7/screenshots/Screenshot-synaptic.jpg[/IMG]

---

### Post by drs305 on 2008-06-15
Yes, you can do it. I uninstalled FF3-64 a while back and got the same messages (and the same angst when I saw ubuntu-desktop). I uninstalled via synaptic and all is well. I just checked and ubuntu-desktop is still not installed. I am running 64 bit hardy with the standard gnome setup.

In theory synaptic will protect you and it appears to have done so for me. ;-)


This won't make you sleep any easier. Here is the entry in synaptic for ubuntu-desktop:
```

This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

```
If it makes you nervous you can always reinstall it afterwards...

---

