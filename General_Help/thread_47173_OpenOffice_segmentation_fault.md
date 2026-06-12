---
title: "OpenOffice segmentation fault"
date: 2005-07-07
forum: General Help
---

### Post by pointym5 on 2005-07-07
On two separate Hoary machines (with similar but different hardware), I'm getting a segmentation fault upon attempting to start OpenOffice.  I've reinstalled it a couple times (OpenOffice, not Hoary) to no avail.  The systems in general work fine under moderate to very heavy development work, so I don't have any reason to suspect any hardware issues.

The specifics are that I type "ooffice" in a terminal window and it immediately dies with a segmentation fault. It never gets a window open.  OpenOffice worked just fine on one of the two machines when it was running Warty.

I've tried removing the user profile info and having it reinitialize, but that results in the exact same behavior.

I've seen mention on various forums about this exact issue, but no mention of an actual solution.

---

### Post by sethmahoney on 2005-07-07
What version of OpenOffice are you trying to use?

---

### Post by pointym5 on 2005-07-07
[QUOTE=sethmahoney]What version of OpenOffice are you trying to use?[/QUOTE]

The current Hoary version, 1.1.3.  In other words it's the version of OpenOffice installed with a fresh Hoary install.

---

### Post by pointym5 on 2005-07-07
I've tried installing 1.1.4 downloaded direct from OO.org, and I get pretty much the same results. The "server" phase of the installation works fine, but running "setup" for the per-user install immediately segfaults.

---

### Post by pointym5 on 2005-07-07
I think I've found it; it has something to do with a library installed with the NVidia drivers (libnvidia-tls).  When those libraries are moved aside, it seems to work just fine.

---

