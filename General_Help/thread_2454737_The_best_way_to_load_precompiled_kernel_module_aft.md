---
title: "The best way to load precompiled kernel module after Kernel upgrade without kernel ?"
date: 2020-12-04
forum: General Help
---

### Post by cpservicespb on 2020-12-04
I think it' s quite old question.
There is Ubuntu 18.04 x64 with kernel of 5.x.x version.
Also there is precompiled kernel module aka driver built by myself from sources.
First building was against 5.3.3 kernel version and was built to deb package for redistribution.
For redistribution but without sources.

After any kernel upgrades, for example from 5.3.3 to 5.4.5 or even from 5.3.3 to 5.3.7, the module stops working because of difference between its vermagic and kernel version.

So, what is the best way to keep driver working within along one kernel version - that the driver built against 5.3.3 version could work under all 5.3.x versions or even under 5.x.x version WITHOUT providing of its sources ?

I know that some important changes is possible at kernel headers from version to version, but it' s other history.

---

### Post by mikewhatever on 2020-12-06
Can use dkms: [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)
Not sure if it is the best, or second best, or third best ...

---

### Post by deadflowr on 2020-12-06
*Thread moved to **General Help***

---

