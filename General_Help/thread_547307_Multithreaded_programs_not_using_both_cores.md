---
title: "Multithreaded programs not using both cores"
date: 2007-09-09
forum: General Help
---

### Post by SeanTater on 2007-09-09
When I add the -threads option to FFMpeg, it runs a *tad* bit faster, but does not use two cores at once no matter what number I set it to. I checked htop and KSysGuard, and they both report that ffmpeg is capitalizing on one core, not both.

This intrigued me, so I recompiled it, to no avail.

Is this how it's supposed to work, or am I doing something wrong?

---

