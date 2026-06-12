---
title: "installing quota on ubuntu 12.04 server"
date: 2013-11-02
forum: General Help
---

### Post by ginger3 on 2013-11-02
I have been trying to install the kernel module quota without success.

      everything i have read suggested that if i install linux-image-extra-virtual i could modprobe quota_v1/quota_v2 and solve the problem,      

but even sfter installing linux-image-extra-virtual, when i  do modprobe quota_v1, it fails (same for quota_v2) :

      FATAL: Module quota_v1 not found.

      and i've checked. it's not in the module listing.  is there a way i can compile the module manually? but where can i find the package and how do i install it? i cant find any tutorial on this. i am at a loss.

    thank you.

---

