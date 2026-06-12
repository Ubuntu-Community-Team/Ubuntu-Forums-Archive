---
title: "Just installed Breezy, going to upgrade a video card.. need reinstall?"
date: 2005-10-26
forum: General Help
---

### Post by generik on 2005-10-26
Hi,

I just got it installed on a system with a Matrox P650 in it, and is in the process of getting the video card changed to a nvidia card due to some issues with the Matrox. Would I need to get the whole distribution reinstalled?

It seems like when I swopped the video card, the system won't boot into the GUI anymore, but leaves me at the desktop. What should I do then?

Thanks.

---

### Post by RAOF on 2005-10-26
You'll need to tell xorg about your new video card.

Run "sudo dpkg-reconfigure xserver-xorg".

---

### Post by metoo on 2005-10-26
You surely found it already out by reading in the wiki, but you should as well install the 'linux-restricted-modules...' package for your kernel (uname -r in a console tells you this).
With that you get the 3D accelerated nvidia drivers.

---

