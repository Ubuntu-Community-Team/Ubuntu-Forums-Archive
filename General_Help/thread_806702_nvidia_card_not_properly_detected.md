---
title: "nvidia card not properly detected"
date: 2008-05-25
forum: General Help
---

### Post by garba on 2008-05-25
just curious about this: the livecd seems to be unable to properly detect my graphics card, X starts with the vesa driver instead sic! adding the "nv" driver to xorg.conf and restarting the X server sorts it for me (i also get the native resolution for my lcd display) but hey wasn't the latest release of xorg supposed to automagically detect hardware without having to rely on the dread xorg.conf thing?

any other nvidia card owner expierencing this problem?

---

### Post by diablo75 on 2008-05-25
Installing the system on a HD will allow it to install the driver properly.

---

### Post by garba on 2008-05-25
i know but i wonder why the livecd isn't using the opensource nv driver and falls back on vesa instead

---

### Post by nebben11 on 2008-05-25
mine did the same thing, problem solved after install to HDD

---

