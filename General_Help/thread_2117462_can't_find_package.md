---
title: "can't find package"
date: 2013-02-18
forum: General Help
---

### Post by Robing Goodfellow on 2013-02-18
I'm resurrecting an old netbook, it's an Acer Aspire One running Precise. It hasn't been used in quite a while, so of course it needs updates. Before I do that though, I wanted to go in and get rid of stuff we won't be using on this machine. One such is ros-fuerte. I ran

sudo apt-get remove ros

and the system tells me it can't find package ros.

I looked to make sure it's there, and there are hundreds of folders, the workspace, etc, so it's there, or at least most of it.

I tried ROS. ros-fuerte, ROS-fuerte, all permutations I could think of. Nada.

How do I get rid of this?

regards, Richard

---

### Post by sudodus on 2013-02-18
How did you install it? If from the repos using apt-get you can remove it that way. But if you installed it by downloading a deb file, use that (if it is advanced enough to provide an uninstaller), or you need to find the package files and remove them manually (risky, you might destroy something else).

You can search for installed packages using ***Synaptic*** (the search window is good for this purpose).
--
By the way, it might be easier to wipe it and reinstall a suitable flavour of Ubuntu (Lubuntu or Xubuntu).

---

### Post by Robing Goodfellow on 2013-02-18
I tried:

$ sudo apt-get remove ros-fuerte-*

and it worked. Thanks for the response.

regards, Richard

---

