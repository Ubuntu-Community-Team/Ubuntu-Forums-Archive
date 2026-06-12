---
title: "Graphical artifacts after upgrade to 16.04"
date: 2017-05-04
forum: General Help
---

### Post by Enforcer5782 on 2017-05-04
We just upgraded our workstation from 14.04 to 16.04, and have started seeing these strange rainbow borders around every window on the desktop. What's particularly strange is that it seems to be at the software layer (not the GPU) because I am able to take screenshots of the issue. We are running a GTX Titan Z on Nvidia's 375.95 driver, which claims to be the latest version.

At first start-up, everything is normal. But, after waking the system from suspend, we get this:
[ATTACH=CONFIG]274957[/ATTACH]

I've tried to restart X and see if that fixes it with ```
sudo restart lightdm
```, which did nothing, and ```
sudo init 3
```, which crashed the system entirely (black screen, no response).

---

### Post by vasa1 on 2017-05-04
[http://askubuntu.com/questions/896221/strange-artifacts-along-window-borders-after-waking-computer-from-sleep-mode](http://askubuntu.com/questions/896221/strange-artifacts-along-window-borders-after-waking-computer-from-sleep-mode)

---

