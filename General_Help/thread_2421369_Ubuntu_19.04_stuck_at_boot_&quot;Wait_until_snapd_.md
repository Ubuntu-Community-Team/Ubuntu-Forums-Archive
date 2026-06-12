---
title: "Ubuntu 19.04 stuck at boot &quot;Wait until snapd is fully seeded&quot; after upgrade"
date: 2019-06-20
forum: General Help
---

### Post by soegaard on 2019-06-20
Hi,

I have upgraded my desktop ubuntu 19.04 and now it is stuck in boot with "Wait until snapd is fully seeded".
Anyone else experienced this issue in the latest upgrades?

I wonder how to fix this as it seems to be consistent even after a clean install.

---

### Post by #&amp;thj^% on 2019-06-20
Really >>after a clean install?:confused:
Most reported with an up-grade rather than a clean install, bug found here:[https://bugs.launchpad.net/snapd/+bug/1779872](https://bugs.launchpad.net/snapd/+bug/1779872)

---

### Post by soegaard on 2019-06-20
I got a bit wiser now.
It seems to be related to when you install vulkan drivers

It happens when I follow this and restarts
[https://linuxconfig.org/install-and-test-vulkan-on-linux](https://linuxconfig.org/install-and-test-vulkan-on-linux)

---

### Post by #&amp;thj^% on 2019-06-25
If this is not resolved, per chance did you notice this from that PPA?
> === Upgrading to a newer Ubuntu ===
It is *strongly* suggested to remove all packages from this PPA before updating to a newer Ubuntu release. See the section "Revert to original drivers" later on.
Then, after the upgrade, you can add again this PPA.
PPA's can be troublesome at times.

---

### Post by themehrankhan on 2020-02-28
I have the same problem after i tried to install League of Legends, it needed to install the NVIDIA 430 drivers and Vulkan Drivers as well, my system is not booting at all, it just freezez at wait until snapd is fully seeded. Can anyone help me ?

Edit: I'm on ubuntu 18.10

---

### Post by coffeecat on 2020-02-28
@themehrenkhan, if you need help, please start your own support thread, rather than hijacking an old, abandoned one. 

Also, Ubuntu 18.10 went end of life in July last year. It is now unsupported. We cannot help with an obsolete release. Please install a currently supported version of Ubuntu, and if you are still experiencing the same problem, you are very welcome to start a new thread seeking help for this. 

If you need help rescuing your personal data from a system that will not boot, you are also very welcome to start a new thread for this.

Thread closed.

---

