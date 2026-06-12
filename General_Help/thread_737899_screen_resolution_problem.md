---
title: "screen resolution problem"
date: 2008-03-28
forum: General Help
---

### Post by dansued on 2008-03-28
When I start up ubuntu, the login screen is at a very low resolution, 640 x 480 or 800 x 600 maybe. Then after logging in, the resolution changes to the lcd native resolution of 1400x1050. Is there a reason why it's doing this? How do I change the resolution for the login screen?

---

### Post by dansued on 2008-03-28
I should note that I tried dpkg-reconfigure xserver-xorg with unsatisfying results

the login screen does have the correct resolution but the process messed up the drivers or something because compiz no longer works and other screen effects refresh very slowly.

---

### Post by danwood76 on 2008-03-28
You may have selected the wrong driver in the xorg reconfigure.

What graphics card do you have? Which drivers do you have installed for it?

---

