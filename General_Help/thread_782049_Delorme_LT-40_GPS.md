---
title: "Delorme LT-40 GPS"
date: 2008-05-04
forum: General Help
---

### Post by travtek on 2008-05-04
FYI,  I just purchased the new Delorme LT-40 GPS unit and found that in order for it to work on Ubuntu, you have to recompile the cypress_m8 module the same way you have to to make the LT-20 work.  I am running Ubuntu 8.04 with the latest (2.6.24-17-generic) kernel and I recompiled my cypress_m8 module according to the instructions in:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/111694)

Now the LT-40 works for me and it seems to lock up faster and work better than the LT-20.



Note: When you do a kernel upgrade on your system you will have to compile the cypress_m8 module again as it will be replaced by the maintainers version during the upgrade.

---

### Post by ghost_ryder35 on 2008-05-04
thanks for the info

---

