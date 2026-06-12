---
title: "Finding out the version of packages installed"
date: 2006-11-18
forum: General Help
---

### Post by Migalicious on 2006-11-18
After having my mouse and my network hosed, then figuring out the hard way that it was all due to the POS 3v1n0 repository (and I feel REALLY dumb, as I should have known better by looking at it), I want to verify what version of all my packages I have installed.  I sorta figured that I could do a find for anything containing 3v1 but that just shows me whats in my apt cache.  Is there a command that does this?  Or am I seriously better off reloading from scratch, due to possible rootage?

---

### Post by CatKiller on 2006-11-18
I **think** (not having done this myself) that if you remove that repository and then look in Synaptic, all the packages that you've installed from that repository will be classed as "**local or obsolete**", so you should then be able to go through just those packages and force the version to the Ubuntu ones.

---

### Post by bayvista on 2006-11-18
System - Administration - Synaptic will tell all.

---

### Post by Migalicious on 2006-11-18
catkiller: It somewhat worked, thanks.

Is there anyway to do this on the CLI?

---

### Post by CatKiller on 2006-11-18
> **Migalicious said:**
> catkiller: It somewhat worked, thanks.

Glad I could help a bit, at least.

> Is there anyway to do this on the CLI?

I'm sure there is, but I don't know exactly what it would be. **man apt-get** or **man aptitude** will probably tell you as much as they'll tell me. **forbid-version** is the aptitude option that caught my eye, though.

---

