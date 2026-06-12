---
title: "Fix (revert) permissions?"
date: 2015-05-10
forum: General Help
---

### Post by Mex5150 on 2015-05-10
Hi All

I meant to set the permissions of everything on an external drive to 777, however it seems I accidentally set **EVERYTHING** in the full file system, rather than just the one drive.

The only issue I've had so far (that I've noticed) is sudo has stopped working, but I'm sure other problems will crop up soon enough.

Is there an easy way to fix this?


~Mex

---

### Post by Scooby-2 on 2015-05-10
I don't think there's an easy fix. Personally I would make a copy of your /home, list all your installed programs and reinstall as your system is currently world-readable. You *could* reset permissions individually but there may be a security risk if you miss something. So I think the quickest fix would really be a reinstall, definitely the safer fix.

---

