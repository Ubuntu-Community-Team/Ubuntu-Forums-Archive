---
title: "Simple synaptic question"
date: 2008-04-28
forum: General Help
---

### Post by krelverehan on 2008-04-28
When I use synaptic to "Download the package files only", where does it save those files?

---

### Post by ibutho on 2008-04-28
Check in /var/cache/apt/archives.

---

### Post by ajgreeny on 2008-04-28
They will go to /var/cache/apt/archives as .deb files which you can double click to install.  They will all be owned by root so you will only be able to copy them if you need to, not delete as user without sudo.

---

