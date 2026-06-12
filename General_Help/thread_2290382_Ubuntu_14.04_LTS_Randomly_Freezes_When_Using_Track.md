---
title: "Ubuntu 14.04 LTS Randomly Freezes When Using Trackpad"
date: 2015-08-12
forum: General Help
---

### Post by jonathan90 on 2015-08-12
Hey guys! I'm using Ubuntu 14.04 LTS and I've been having problems with the screen freezing on random occasions.  I've noticed that it only happens when I use the trackpad and that it's a graphics driver issue.  I've also seen posts of about on Launchpad, but the solutions I've found aren't working.

Here's the link to the Launchpad page I was looking at. [https://bugs.launchpad.net/xorg-server/+bug/1220426/](https://bugs.launchpad.net/xorg-server/+bug/1220426/)

I tried running the code below (from the Launchpad link), but it said "unable to resolve host *my username.*" It also made my trackpad cursor move really slowly while my mouse remained at the same speed, and after speeding up the mouse movement in the settings, the trackpad is back to normal speed but the USB mouse would be way too fast to use.

echo "options psmouse proto=imps" | sudo tee /etc/modprobe.d/psmouse.conf >/dev/null sudo modprobe -r psmouse && sudo modprobe psmouse

---

