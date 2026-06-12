---
title: "Gnome Startup Problem"
date: 2007-05-17
forum: General Help
---

### Post by sessine on 2007-05-17
I'm having a problem when I try to start the gnome desktop in Ubuntu 7.04

The system boots fine into gdm.  When I log into gnome I get the default background and the spash that shows whats loading (e.g. nautilus etc) but the screen is frozen.  If I do top in a terminal it shows that gnome-settings-daemon and x-session-manager are using 100% cpu.

I think that some settings files have become corrupted somewhere, I just don't know where.  All I can figure out is that it has to be early on in the gnome startup.

I do have beryl installed but I don't think it is the problem since the beryl-manager is started near the end of the process and it dosen't show up on either top or ps.

It must be something gnome specific since I also have fluxbox and thats working fine but the failsafe gnome option has the same problem.

Any help would be appreciated.
:confused:

---

### Post by Quintin Riis on 2007-05-17
Simplest would be to delete all your settings, then login.  

rm -r .gconf and friends.

---

