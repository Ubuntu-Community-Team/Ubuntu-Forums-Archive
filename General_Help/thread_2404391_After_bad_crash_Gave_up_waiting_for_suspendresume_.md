---
title: "After bad crash: Gave up waiting for suspend/resume device, root device--Ubuntu 18.04"
date: 2018-10-23
forum: General Help
---

### Post by phrhcc on 2018-10-23
Hi,
I was happily working on my XPS15 laptop with Ubuntu 18.04 and accidentally spilled water over the keyboard.
Fortunately there is no hardware damage but I cannot get back to ubuntu.
I have window partition which was also not working until I reinstalled window. Now it works and I can see all data (the window one) is there.
However I still cannot get Ubuntu to start.
I tried to go in recovery mode but eventually I get:

Gave up waiting for suspend/resume device, root device.
ALERT! UUID==aa7f7ba-6906-4593-88e3-cc7e4376290e does not exist. Dropping to a shell!

And then I get the initramfs shell.
I am a very much a beginner of ubuntu, but after reading the forum I tried to run blkid. However it displays nothing and returns no error.
I thought that maybe I needed root permission but sudo is not recognised as a command. 
lsblk also returns "not found"
Also I see no way to display my /etc/fstab

Any help? My main concern would be to access somehow the data.

---

