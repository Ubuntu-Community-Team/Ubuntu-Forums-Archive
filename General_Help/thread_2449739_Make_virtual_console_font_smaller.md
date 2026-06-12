---
title: "Make virtual console font smaller"
date: 2020-09-01
forum: General Help
---

### Post by straeker on 2020-09-01
I just installed kubuntu-desktop on my box and the installation magically made my tty's font very large. "dpkg-reconfigure console-setup" seems does not work at all. Any idea?

---

### Post by CatKiller on 2020-09-01
I suspect that it's not that the fonts are large, but that the resolution is low. There are ways to set the resolution, though, through your Grub configuration.

---

### Post by straeker on 2020-09-01
it's already the highest resolution of my display 
GRUB_GFXMODE="1366x768x16"

---

