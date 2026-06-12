---
title: "Mounted devices showing up on desktop"
date: 2007-01-14
forum: General Help
---

### Post by Vord on 2007-01-14
So, I'm using Edgy with Gnome, and I have several devices that automatically mount when plugged, External hard drive, ipod, flash drive, etc. I'm wondering how I would go about stopping them from showing up on my desktop.

---

### Post by energiya on 2007-01-14
try
```
gconf-editor
```
in terminal, and apps > nautilus > desktop > volumes_visible uncheck. **I think** this would work.

---

### Post by Vord on 2007-01-14
Excellent, worked like a charm, thanks :D

---

