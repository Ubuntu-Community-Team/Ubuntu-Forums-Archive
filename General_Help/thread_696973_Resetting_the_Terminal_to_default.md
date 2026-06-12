---
title: "Resetting the Terminal to default"
date: 2008-02-14
forum: General Help
---

### Post by Rikkard on 2008-02-14
I was messing around with my terminal profile settings, and all seemed well enough, but I think I put something where I shouldn't have and now whenever I try to open a terminal it flashes open for about half a second, then closes. My guess is I put something in the "run instead of my shell" 

Is there a way to access that profile and reset it? I can still access the terminal via ctrl+alt+1.
Or is there a way to create a new profile that I can set to default temporarily?

Edit: I ran gconftool-2 --recursive-unset apps/gnome-terminal (or something similar) and it seems to have worked. Just need to reconfigure it all. Horray.

---

### Post by oldos2er on 2008-02-14
Go to your home directory, Places, Home. Type Ctrl-h to show hidden files. Copy .bashrc~ over .bashrc .

---

