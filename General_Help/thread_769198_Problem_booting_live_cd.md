---
title: "Problem booting live cd"
date: 2008-04-26
forum: General Help
---

### Post by Matt1632 on 2008-04-26
I just tried to boot my new 8.04 live cd to try it out, but when I choose "try Ubuntu without changing my computer" on the menu I get an error after it finishes loading the kernel.  The error code is:

```
[  29.689193] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[  29.689241] ACPI: EC: read timeout, command = 128
```

The numbers in the square brackets were different the first time I tried to boot it.

I've never had a problem booting an Ubuntu live cd on my computer before, I checked the md5sum on the iso before I burned it, I verified the cd after burning, and ran the error check utility on the cd.  What could be going wrong?

(P.S. Assuming I get this to work, I want to install Ubuntu 8.04.  Does the "install ubuntu" option on the menu launch the alternate text-based installer or are there just two live session options, one with and without an installer icon on the desktop?)

---

### Post by Matt1632 on 2008-04-26
I just found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137").  It seems that the problem occurs mainly on Sony Vaio laptops, which makes sense for me because I'm using a Sony Vaio VGN-FE870E.  Is there any resolution to this bug?

---

