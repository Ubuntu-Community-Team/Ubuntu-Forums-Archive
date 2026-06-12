---
title: "upgrade failed to start x"
date: 2006-12-05
forum: General Help
---

### Post by DougieFresh4U on 2006-12-05
doing upgrade on other machine and x failed to start. how can I fix from command line in grub? thanks

---

### Post by Shatrat on 2006-12-05
Well, if you upgrade the kernel then proprietary video drivers need to be reinstalled because they are kernel specific.
I think reverting your xorg.conf to use the free version of your particular graphics cards driver should allow you to get to a 2d desktop, and then you could install the proprietary drivers again normally.
more specifically, change from fglrx to ati, or nvidia to nv. (I think those are the right modules)

---

### Post by DougieFresh4U on 2006-12-05
don't quite understand all that you, but not to worry as I'm just gonna re-install again as I saw some dependancy problems as well

---

