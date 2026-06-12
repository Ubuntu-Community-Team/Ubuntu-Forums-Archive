---
title: "[SOLVED] depmod segmentation fault"
date: 2007-11-17
forum: General Help
---

### Post by Wd2048 on 2007-11-17
I have a problem with my ubuntu box. I have to use the Nvidia restricted drivers, and after a reboot, I got the error that i was running in low-graphics mode. I tried reinstalling the Nvidia drivers, but no good. So i grabbed the latest binary from Nvidia.com, and it errored out while doing the depmod -aq.

So, I tried to "sudo depmod -aq" and got the following:
Segmentation fault (core dumped)

Any ideas as to what i can do to rectify this?

---

### Post by mindwarp on 2007-11-17
You need to go to System -> Administration -> Restricted Manager and enable the nvidia driver there.  It isn't recommended to use the driver straight from nvidia's site unless you are an advanced user.  I would recommend troubleshooting the original issue with the nvidia driver.

---

### Post by Wd2048 on 2007-11-18
mindwarp, I've been there and according to the screen, it is in use. However, X will not use my screen0 setup with the Nvidia driver.

---

### Post by Wd2048 on 2007-11-28
So, in the interest of time, I had some additional space on another harddrive, so I backed up my myth-data and did a mysqldump... i've reinstalled 7.10-64bit and am continuing on rebuilding. :(

---

