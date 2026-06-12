---
title: "kde resolution bad"
date: 2007-12-30
forum: General Help
---

### Post by nonewmsgs on 2007-12-30
my xorg.conf file is fine.  my gnome res is fine.  my xfce res is fine my other kde user's res is fine, but mine isn't.  if i try to adjust the display properties it corrupts the xorg.conf file and i have to redo that.

for some reason it thinks i want 640x480, but assuredly i do not.  it was working fine for a long time and this is gutsy standard kde not 4.0.

---

### Post by davarino on 2007-12-31
Take a look at these posts, might make a difference:
<http://ubuntuforums.org/showthread.php?t=588699>

---

### Post by nonewmsgs on 2008-01-04
thanks that put me ont o the right track.

solution:
first i deleted the entire /home/.kde/share/config directory 
sudo nautilus
copied other users config directory to mine

chown the directory


this was mostly trial and error.  the config text does not work.  just overwriting the changed files does not work.

---

