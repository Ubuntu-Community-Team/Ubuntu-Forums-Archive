---
title: "Different wallpapers for different workspaces?"
date: 2008-04-09
forum: General Help
---

### Post by Fazz Munkle on 2008-04-09
First off I tried wallpapoz already and it's not what I want. I have Compiz installed and the wallpaper only changes after I changed to a different workspace with wallpapoz. Is there anyway to set the wallpaper beforehand and have it static instead of dependent on after you're switched workspaces? I've heard of a wallpaper plugin for Compiz, but I've heard it's really computer crashing buggy. You'd think this would be simple enough to accomplish. An option in the Appearance control panel or something. As for Desktop Drapes, is that a multiple wallpaper utility? Didn't look like it was.

I'm using Ubuntu 7.10 with Gnome.

---

### Post by chrisccoulson on 2008-04-09
This functionality does not exist yet.

For the Compiz wallpaper plugin to function, you either need to stop Nautilus from drawing the desktop (achievable through gconf but then you'll lose your desktop icons), or patch Nautilus to not draw the wallpaper when Compiz wants to draw it (see [here]("http://ubuntuforums.org/showthread.php?t=600909")

Also have a look at this discussion [here]("http://ubuntuforums.org/showthread.php?t=747337")

---

