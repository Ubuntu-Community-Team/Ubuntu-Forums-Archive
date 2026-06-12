---
title: "[SOLVED] help me get direct rendering working"
date: 2008-05-30
forum: General Help
---

### Post by Polygon on 2008-05-30
As you can see from my attachment, i have the ati drivers installed using hardware manager but i still dont have direct rendering. This is boggling my mind as i have removed and reinstalled them countless times and even tried using envy to do this but it still doesnt work. I want my direct rendering back =/

I have an ati radeon 9800

---

### Post by Polygon on 2008-05-30
it seems to be related to this bug report: [https://bugs.launchpad.net/ubuntu/+bug/228573](https://bugs.launchpad.net/ubuntu/+bug/228573)

and the solution is to just install linux-restricted-modules then go back to hardware manager and renable the ati drivers. Restart and it works...or at least it did for me.

---

