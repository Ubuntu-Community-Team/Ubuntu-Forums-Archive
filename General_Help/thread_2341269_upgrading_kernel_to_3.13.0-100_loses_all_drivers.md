---
title: "upgrading kernel to 3.13.0-100 loses all drivers"
date: 2016-10-26
forum: General Help
---

### Post by mrinella2 on 2016-10-26
In patching the dirty cow bug, we are upgrading to the 3.13.0-100-generic kernel.  This has been just fine on our virtual hosts, but when we got to our first physical host, the upgraded hosts failed to boot afterwards.  I think I can see why, as none of the drivers made it to the new /lib/modules dir:

:/lib/modules# du -sh *
31M     3.13.0-100-generic
184M    3.13.0-74-generic
184M    3.13.0-77-generic
151M    3.5.0-54-generic

The initd file for this kernel is also a bit small:

-rw-r--r--  1 root root  5863230 Oct 26 17:23 initrd.img-3.13.0-100-generic
-rw-r--r--  1 root root 19225927 Feb 18  2016 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root 19231390 Sep 28 16:42 initrd.img-3.13.0-77-generic
-rw-r--r--  1 root root 15684362 Dec 29  2015 initrd.img-3.5.0-54-generic


You can also see we have successfully updated the kernel here before.

I did try copying everything from /lib/modules/3.13.0-77-generic/kernel/drivers/ to /lib/modules/3.13.0-100-generic/kernel/drivers/ and booting with the same result, and also after that tried running "update-initramfs -c -k 3.13.0-100-generic" and "depmod -a", and the host still wont boot.

When we boot, it cant find the root drive.  Im assuming its due to the fact the driver for the raid controller wont load, but I'm certainly open to other causes.  Obviously using the previous kernel (3.13.0-77-generic) is fine. Its a dell server with an embedded perc h310 raid controller, firmware on everything has been updated too.

Thanks in advance for any suggestions.

---

### Post by a66at on 2016-10-27
I had the same problem and was able to work it around by installing linux-image-3.13.0-100-lowlatency (and removing linux-image-3.13.0-100-generic).

---

### Post by mrinella2 on 2016-10-27
Thanks, I'll give that a shot.

---

### Post by Bucky Ball on 2016-10-27
Not Dirty Cow again. What release are you using?

---

### Post by mrinella2 on 2016-10-28
> **Bucky Ball said:**
> Not Dirty Cow again. What release are you using?


14.04.5

---

### Post by mrinella2 on 2016-10-28
> **mrinella2 said:**
> Thanks, I'll give that a shot.

This was successful for me as well.  I wonder if the next generic kernel release will work.  Im sure the low latency kernel is fine, but the worrywarts here are already worrying.

---

