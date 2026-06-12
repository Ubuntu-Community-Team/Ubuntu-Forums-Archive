---
title: "Update today broke desktop"
date: 2018-02-15
forum: General Help
---

### Post by jcs3rdma2 on 2018-02-15
After the system ran the updates today, after rebooting, the unity desktop appears to be broken. No icons along the left side and nothing along the top. I am able to right clip and get the desktop menu to appear, however that is all. None of the window controls, minimize or max or del, appear on the system settings menu or command window. Running 16.04 LTS.   Any ideas would be appreciated.

7:4pm Central - **Update**: I loaded the Cinnamon desktop environment and can use the system once again. At least I know that the OS is not hosed. 
Too bad I cannot find the information to fix the default (Unity?) desktop environment.
I tried to reinstall the ubuntu-desktop, which fails with "you may have broken packages" and depends on Unity.
I tried to reinstall Unity, which fails with "you may have broken packages" and depends on a Compiz-core...... (long name, cannot remember)
I tried to reinstall the Compiz-core..... , which fails with "you may have broken packages" and that the Compiz-core...... is not a valid package.
As I said, I can use the system, just not with Unity...   Any ideas??

---

### Post by vasa1 on 2018-02-15
Please see [https://ubuntuforums.org/showthread.php?t=2385070](https://ubuntuforums.org/showthread.php?t=2385070)

---

### Post by davidsrsb on 2018-02-16
Same here and no warnings about anything held back on a 16.04.1 PC.
Unity is gone, reinstalled from synaptic and normal service is restored
Not very good for an LTS

---

### Post by jcs3rdma2 on 2018-02-16
Thank you, vasa1, for posting the link that pointed to a resolution. I was able to resolve this problem by using the following "sudo aptitude install ubuntu-desktop"

All appears to be working as before, thanks once again.

---

