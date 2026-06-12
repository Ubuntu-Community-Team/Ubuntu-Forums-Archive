---
title: "Deleting unwanted wallpapers?"
date: 2013-01-02
forum: General Help
---

### Post by oxf on 2013-01-02
How do I delete unwanted wallpapers that are automatically installed?
Search reveals that they are kept in      /usr/share/doc     but then there are several sub folders and its unclear which one they are in. I only which to keep two of the orriginal ones.

Thanks

---

### Post by Frogs Hair on 2013-01-02
The default wallpapers are in usr/share/backgrounds and the unwanted ones can be moved to trash from there. Use ```
gksudo nautilus
``` to make changes in the file system. To remove the entire package use the following. ```
sudo apt-get remove ubuntu-wallpapers
``` There are wallpapers from previous Ubuntu versions available in synaptic also.

---

### Post by oxf on 2013-01-02
> **Frogs Hair said:**
> The default wallpapers are in usr/share/backgrounds and the unwanted ones can be moved to trash from there. Use ```
gksudo nautilus
``` to make changes in the file system. To remove the entire package use the following. ```
sudo apt-get remove ubuntu-wallpapers
``` There are wallpapers from previous Ubuntu versions available in synaptic also.

OK thanks, thats where they are!
Yes the previous Ubuntu versions are part of the problem, I installed too many

---

### Post by Frogs Hair on 2013-01-03
If you have synaptic installed or delete the unwanted wallpaper packages from there.

---

