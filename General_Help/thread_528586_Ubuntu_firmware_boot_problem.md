---
title: "Ubuntu firmware /boot problem"
date: 2007-08-18
forum: General Help
---

### Post by V3lier on 2007-08-18
Well I compiled my own kernel and everything is great. I tried removing usplash but it gave me this:
Removing usplash ...
update-initramfs: Generating /boot/initrd.img-2.6.22.2
find: /lib/firmware/2.6.22.2: No such file or directory
find: /lib/firmware/2.6.22.2: No such file or directory
find: /lib/firmware/2.6.22.2: No such file or directory
find: /lib/firmware/2.6.22.2: No such file or directory
find: /lib/firmware/2.6.22.2: No such file or directory
find: /lib/firmware/2.6.22.2: No such file or directory

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.22.2
dpkg: error processing usplash (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 usplash
E: Sub-process /usr/bin/dpkg returned an error code (1)

It seems my /boot is full. I put 100MB to it because I heard that is plenty but it doesn't seem like it. I tried adding gparted but the same error comes up "find: /lib/firmware/2.6.22.2: No such file or directory". I kept googling for a solution and have found [this]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/111240").  So it seems that the firmware is causing the trouble. I plan on adding Ubuntu from scratch and compiling the kernel again but this time checking to add the firmware but it would be great if there was an easier, less time consuming problem.

---

### Post by V3lier on 2007-08-18
*bump*

---

### Post by V3lier on 2007-08-18
Well I'm currently configuring the kernel. Which options should I allow to make firmware work?

---

### Post by V3lier on 2007-08-18
*Bump* Please help. If anymore information is needed then please ask. I really need help.

---

### Post by V3lier on 2007-08-18
*bump*

---

### Post by g2g591 on 2007-08-18
i think you should probabily reinstall and not try messing around with your own kernal

---

### Post by V3lier on 2007-08-18
> **g2g591 said:**
> i think you should probabily reinstall and not try messing around with your own kernal
No worries. I fixed the problem. Once you compile the kernel you have to update and everything will get fixed. No more errors :).

---

