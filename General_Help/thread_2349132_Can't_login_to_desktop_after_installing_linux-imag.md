---
title: "Can't login to desktop after installing linux-image-4.8.0-34-generic"
date: 2017-01-11
forum: General Help
---

### Post by waltman on 2017-01-11
I'm running 16.10, and last night I installed the update from the 4.8.0-32 to 4.8.0-34 kernel. After rebooting I was no longer able to login to the desktop. I was, however, able to ssh in, and after checking my logs it looks like I have the same problem previously reported at [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1511824](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1511824)

I booted back into 4.8.0-32 and then was able to login to the desktop as normal again. I've seen other reports of this issue online besides the one I listed above, but none of them have any resolution to the problem. I don't have any idea how to go about fixing this, but I'd be glad to post any log entries that might be of use.

One possibility is that this box has an NVIDIA GPU GeForce GTX 1060 with the latest Nvidia drivers.

---

### Post by waltman on 2017-01-12
This did turn out to be the Nvidia drivers. When I ran Nvidia's installer, it put its modules under /lib/modules/4.8.0-32-generic. I couldn't figure out how to get it to recompile and also put modules under 4.8.0-34-generic. I uninstalled the drivers, and reinstalled them via the PPA described at [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa).

It remains to be seen whether I'll have more problems the next time there's a new kernel, but for now I'm rocking 4.8.0.34.

---

