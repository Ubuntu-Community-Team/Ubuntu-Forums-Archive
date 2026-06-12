---
title: "lightdm doesn't always show up when switching user or logout"
date: 2013-02-27
forum: General Help
---

### Post by sylwester on 2013-02-27
So I have a machine which there are 3 users. We had a problem with lightdm-zombies, but it seems to be fixed now. However, sometimes lightdm doesn't appear after logout/userswitch to non-active user as if someone had run sudo service lightdm stop. It shows a black screen with lines originally from boot process.

Anyway i press CTRL+ALT+F1 and login as root and write service lighdm start and it's up again. Any session that were active however seems to be lost/dead. My problem is that the rest of the family isn't so used to a terminal and freaks out and usually boots the damn thing.

I'm using quantal, upgraded from initial precise.

Anyone had similar problems and know how to fix it?

---

