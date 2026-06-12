---
title: "How to reset Kernel to 3.16 and Ignoring BGRT error."
date: 2015-08-27
forum: General Help
---

### Post by sebastiaan5 on 2015-08-27
Hello,

Recently I was reading something on linuxworld, it was a tiny tutorial to install kernel 4.16 on Ubuntu. I thougt why not? So I downloaded a file kernel 416.tar.gz, mI followed all the steps correctly but as soon as I suspend my laptop and reopen it I get a black screen and can't even do ctrl alt f1.
Also when I reboot my laptop I get an error:

```
ignoring BGRT invalid status 0 (expected 1)
```

Also I get a lot of unexpected problem pop up screens, the conclusion of the details is that there are problems with the kernel.
Is there a simple option to remove this kernel and install the default kernel again?

specs:  Lenovo y50-70 i7 860m gtx  Ubuntu 14.04

---

### Post by Bucky Ball on 2015-08-27
Boot the machine, hit shift to get to the grub list, choose the previous kernel.

With the 4.16 kernel I would expect breakage and wouldn't be using it unless I was testing. Which you probably aren't. :)

---

