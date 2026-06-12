---
title: "Where did 'screens and graphics' go?"
date: 2008-04-25
forum: General Help
---

### Post by gpilkay on 2008-04-25
Hello, I was hunting through some of the posts but haven't found this yet.

Where did 'screens and graphics' go in Systems>Administration?  I need it to correct an improperly detected monitor (this has happened before and is easy to fix) but I can't find, in 8.04, the tool that lets you select the monitor type and model.

Thanks!

---

### Post by MWeather on 2008-04-25
Run 'gksu displayconfig-gtk' (without the quotes)

The icon is probably in the menu, just hidden. Edit the menu and dig around, you should find it.

---

### Post by Eclipse. on 2008-04-25
> **MWeather said:**
> 

The icon is probably in the menu, just hidden. Edit the menu and dig around, you should find it.

Yes its hidden inside others, its now obsolete because X tries to do everything itself now.

> Meanwhile, I've also disabled displayconfig-gtk in the menus. It is still available from the command line (we still need it for bulletproof-X mode). It's become largely obsolete due to Xorg 7.3 autoconfiguration changes, which has resulted in a lot of stuff that used to be set in xorg.conf to no longer be listed there. This confuses displayconfig-gtk greatly, and has been the source of a lot of bug reports and trouble. Further, while displayconfig-gtk has a nice multi-head layout capability, it depends on (the now heavily deprecated) Xinerama, yet these days there are very few drivers that still use Xinerama, so it's become obsolete on this count as well (indeed, you can produce broken xorg.conf's this way). So, the number of people who can still make use of it is becoming quite small, but is not yet negligible, so hopefully having this tool available on the system will still address these users' needs.I made a bit of a fuss when it first got moved into applications --> others, during development only to find out it had became obsolete.

---

