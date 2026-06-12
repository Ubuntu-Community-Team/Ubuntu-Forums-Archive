---
title: "Prevent from automatic kernel updait"
date: 2017-03-27
forum: General Help
---

### Post by shestipal on 2017-03-27
Good day, friends. 

Please help me to stop aptitude automatic kernel update. I have installed ukuu and last mainline version of kernel 4.10.6, but apt offered me to downgrade to 4.8. I do not want to lock update and freeze kernel version because I update it as soon as it mainline kernel is appearing.

Thanks in advance

engineer@host:~$ uname -a
Linux host 4.10.6-041006-generic #201703260832 SMP Sun Mar 26 12:34:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by howefield on 2017-03-27
Welcome to the forums, thread moved to the "*General Help*" forum as a support thread.

---

### Post by deadflowr on 2017-03-27
Did it actually offer to downgrade or simply offer to install the older kernel?

In order to prevent the system from trying to install the supported kernel versions (supported being those that are built for the release at hand), remove 
*linux-image-generic linux-headers-generic linux-generic * though the first two will be installed, the third most likely won't be, but double check to be sure.

These packages are tied to the latest kernel of the version used on whichever release of Ubuntu you are running.
Removing them should prevent the supported kernel versions from being updated/installed.

---

