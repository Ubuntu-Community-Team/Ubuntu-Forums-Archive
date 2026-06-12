---
title: "Installing newest fglrx on Kubuntu 15.04 leads to black screen"
date: 2015-08-22
forum: General Help
---

### Post by El Zoido on 2015-08-22
Hello!

For a few days now, I'm struggling with the fglrx drivers and my HD 7850 GPU.
I've recently bought the GPU in used condition to replace my older nVidia card which had some hardware issue.
I'm using dual-boot between Win7 and Linux and the card works fine in Win7 - so far I get good performance and don't have any issues.

Originally I was using Mint 17.2 for my Linux distro, but encountered rather bad performance with the AMD gpu and therefore recently switched to the newest Kubuntu to check out whether another (and newer) distro would help.
The card does work both with the radeon driver (I do get some minor issues though, why I don't want to stay on that one) and fglrx-updates from the repositories.
However, performance is still not where I would like it to be (much worse than in Windows 7), so I wanted to install the newest fglrx as provided directly from AMD.
Crappy performance aside, I had gotten it to work just fine on Mint (by using the packages provided for 14.04.3), so I downloaded the respective version for 15.04 and installed it (which worked as far as I can tell).

However, whenever I boot with this driver, the screen goes black after the boot logo and the system becomes locked up.
I can't even switch to a text console (e.g. by Strg-Alt-F1) to do any diagnostic, let alone fix it from there.

I was able to get rid of the driver only by using the recovery mode and booting into a root shell, mounting the filesystem as writeable and removing fglrx via apt-get.
I retried a few times, following various guides to installing fglrx manually (which are all pretty similar, obviously), but to no avail.
Now I'm back to using the fglrx provided by the repos, but I'd still like to update to a newer driver.

Does anybody has an idea what's causing the black screen and how to proceed?

---

### Post by El Zoido on 2015-08-23
I've managed to solve the problem...

Seems that a) I did overlook one error message during the install of the driver and b) there's actually a known bug (whether the bug is in the kernel or the driver I can't say):
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1479913](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1479913)

I managed to fix the 15.7 driver as provided by AMD by applying the patch from answer #7 in the bug report above.
Afterwards it was possible to install and is working now.
Only one small problem remained, which is that for some reason the fglrx from the repos has a higher version number (wrongly). To prevent the system from updating it, I locked the manually installed version.

---

### Post by hansdown on 2015-08-23
Good work, 
El Zoido.

Glad tou fixed it.

---

