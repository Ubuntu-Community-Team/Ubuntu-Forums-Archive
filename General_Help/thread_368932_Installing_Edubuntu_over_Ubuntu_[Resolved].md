---
title: "Installing Edubuntu over Ubuntu [Resolved]"
date: 2007-02-23
forum: General Help
---

### Post by uzd4ce on 2007-02-23
I've been running Ubuntu for about 6 months now.  I've got a 3-year old who uses TuxPaint and the GCompris apps fairly often.

Was considering Edubuntu, but I'm not really sure what the difference is.  Is there really a difference, or can I just install a few packages and basically have the same thing?

If it's worth doing a separate install of Edubuntu, can I just "upgrade" my current install?  I don't want to lose my apps, keyboard shortcuts, shared drive settings, and such.

Thanks

---

### Post by aysiu on 2007-02-23
Type this into a terminal and see what packages it wants to add: ```
sudo apt-get update
sudo apt-get install edubuntu-desktop
``` If you want all of them, go ahead and say *yes*. Otherwise, make note of which ones look interesting and install those.

---

### Post by uzd4ce on 2007-02-24
Thanks, that's exactly what I was looking for.

---

