---
title: "How to re-enable Nvidia Driver after Software Update?"
date: 2016-09-25
forum: General Help
---

### Post by UserJB on 2016-09-25
Hi.  I have Ubuntu 14.05 installed with an Nvidia Driver.  After recent
automatic software updates, the Nvidia driver was disabled and when I
rebooted, the standard driver was enabled.  How do I re-enable the Nvidia
driver?

NOTE: I tried to re-install the NVIDIA driver, but had problems.  It requires
the kernel source code and that now seems to be missing.  I can't install the
kernel source now because the machine is now off the internet.

---

### Post by deadflowr on 2016-09-25
Which method of installing the nvidia driver will hep determine why it's being disabled.

Typically the driver will get disabled if you do not have the dkms package installed.
This packages allows 3rd party drivers such as the nvidia driver to automatically get rebuilt when ever a newer kernel gets installed.
Without it, the driver won't get rebuilt into the new kernel and thus leave it disabled.

---

