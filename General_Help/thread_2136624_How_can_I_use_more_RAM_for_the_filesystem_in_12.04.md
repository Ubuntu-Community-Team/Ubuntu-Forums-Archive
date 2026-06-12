---
title: "How can I use more RAM for the filesystem in 12.04 live USB?"
date: 2013-04-18
forum: General Help
---

### Post by d0006 on 2013-04-18
I am running 12.04 64-bit live (from a 2GB USB) on a Lenovo T400 laptop with 8GB of RAM.
When I check the free space in /home with Nautilus it shows 1.4GB free.  /dev and /tmp show 4.1 GB free, why?  How can I make more space in /home? How can I allocate RAM for the filesystem versus processing?

System monitor shows 7.7GB of RAM installed.

Thanks

---

### Post by btindie on 2013-04-18
Part of your 8GB of RAM would be used for the onboard VGA, hence why it shows less than you have installed.

Take a look at [http://manpages.ubuntu.com/manpages/oneiric/live-boot.7..html](http://manpages.ubuntu.com/manpages/oneiric/live-boot.7..html) I think the ramdisk-size option should allow you to do what you want.

You need to either manually pass it to the kernel when it boots or modify your USB stick to use it by default.

---

