---
title: "Need a kernel module downgrade for hfsplus support"
date: 2013-10-07
forum: General Help
---

### Post by krayt2 on 2013-10-07
Hello everyone,


I have a problem mounting some hfsplus drives. I just need them mounted readonly. I did a lot of research and found out that due to changes from kernel version 2.6.37 to 2.6.38 the problem started. ([https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/734883](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/734883))


So I tested with Linux with kernel version 2.6.37 and lower and it worked fine. Versions above including my version which is 3.2.0-54-generic did not work fine with mounting hfsplus images and disks. So I need the hfsplus module from a working version like 2.6.31-14-generic from ubuntu 9. 


I just copied "/lib/modules/2.6.31-14-generic/kernel/fs/hfsplus.ko" to my current 3.2.0-54-generic kernel. But that did not work. How do I get the working hfsplus part into my current 3.2.0-54-generic kernel ubuntu 12.04 linux?


greetings


krayt2

---

### Post by krayt2 on 2013-10-08
Anyone?

---

