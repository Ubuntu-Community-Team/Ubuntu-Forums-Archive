---
title: "Kernel Tunning"
date: 2007-06-08
forum: General Help
---

### Post by djcrash1981 on 2007-06-08
Hi to all, now I have a problem trying to tune some kernel parameters.

The ones I'm trying to change are the ones referenced to the number of open process by user and the nofiles (descriptors).

I been checking the output of the command sysctl -a but I can't find them, anyone can tell me where to find it or how to check them?????

I'm using UBUNTU Festy Fawn, kernel 2.6.20-15-386

Thanks in advance for your attention and help.

---

### Post by djcrash1981 on 2007-06-08
Ok, i found out that this limits are defined in the /etc/security/limits.conf ](*,) unlike other *NIX which have them defined directly in the kernel.

Sorry for the inconvenience and the trouble.

Like always we learn something new every day.

:D

---

