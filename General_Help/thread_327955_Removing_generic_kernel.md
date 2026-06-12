---
title: "Removing generic kernel"
date: 2006-12-30
forum: General Help
---

### Post by kodjo on 2006-12-30
Since I upgraded from Dapper to Edgy on my VAIO FS515B, boot time has changed from about 40 seconds to close to 2 mins. After searching this forum I found the following solution:

[http://www.ubuntuforums.com/showthread.php?t=285920&page=2&highlight=sony+vaio]("http://www.ubuntuforums.com/showthread.php?t=285920&page=2&highlight=sony+vaio")

It says I should install linux-image-386 and linux-restricted-modules-386 and the remove the generic kernel and restricted modules. I was able to downloaded the i386 files, but couldn't not find a guide on how to remove the generic ones.

Please help!

---

### Post by KenSentMe on 2006-12-30
It's best to always use a packagemanager (like Synaptic or apt) to add or remove programs (and kernels). So check here [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html) and use this guide to remove the generic kernel and install the new kernel you want.

---

