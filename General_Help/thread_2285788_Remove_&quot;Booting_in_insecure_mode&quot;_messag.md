---
title: "Remove &quot;Booting in insecure mode&quot; message at startup"
date: 2015-07-08
forum: General Help
---

### Post by Jrmie_bellion- on 2015-07-08
Hi,

I installed kubuntu 15.04 a few days ago, and for the first time since i use Linux, it displays a message before the grub menu appears : "Booting in insecure mode".

I have manually disabled the secure mode in my bios for a reason (to be able to use android debugger on wndows 8.1) and so i don't need ubuntu to remind me of that at every startup. Moreover, it uselessly delays the startup of around 2 seconds.

Any ideas of how i could disable this warning?

Thanks a lot and have a nice day !

---

### Post by kagashe on 2015-07-08
> **Jrmie_bellion- said:**
> Hi,

I installed kubuntu 15.04 a few days ago, and for the first time since i use Linux, it displays a message before the grub menu appears : "Booting in insecure mode".

I have manually disabled the secure mode in my bios for a reason (to be able to use android debugger on wndows 8.1) and so i don't need ubuntu to remind me of that at every startup. Moreover, it uselessly delays the startup of around 2 seconds.

Any ideas of how i could disable this warning?

Thanks a lot and have a nice day !

[shim prints "Booting in insecure mode" when booting without SecureBoot enabled]("https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1384973") 

Kamalakar

---

### Post by Jrmie_bellion- on 2015-07-08
Thanks for the link, however it says that the "bug" has been fixed with shim 0.8, however any "dist-upgrade" attempts only install shim 0.7

Have a nice day!

EDIT :

I installed it manually from here : [https://launchpad.net/ubuntu/vivid/amd64/shim/0.8-0ubuntu2](https://launchpad.net/ubuntu/vivid/amd64/shim/0.8-0ubuntu2)

then tried an update-initramfs -u
and rebooted. Did not solve it. I must have missed something but what ?

---

### Post by kagashe on 2015-07-08
> **Jrmie_bellion- said:**
> Thanks for the link, however it says that the "bug" has been fixed with shim 0.8, however any "dist-upgrade" attempts only install shim 0.7

Have a nice day!
shim 0.8 will come with Ubuntu 15.10

Kamalakar

---

