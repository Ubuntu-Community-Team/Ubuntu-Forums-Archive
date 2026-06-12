---
title: "Restart Compiz"
date: 2016-11-14
forum: General Help
---

### Post by moteprime on 2016-11-14
Ubuntu 16.04 amd64 Thinkpad L450 core i5 16Mb RAM

When starting Ubuntu up and login in, Compiz uses cirka 90 Mb RAM.
I'm not sure how it goes wrong, (i suspect suspend) but Compiz memory usage grows up to 450-550 Mb within a couple of days and eventually i restart Ubuntu.
Are there any way to restart or reset Compiz to reclaim memory, without having to restart the hole system?

---

### Post by farrinux on 2016-11-14
Have a look here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1572801) Seems as though it's a bug in the kernel.

Not sure but if you restart x will that not restart compiz?

---

### Post by moteprime on 2016-11-14
@ farrinux's Thanks. - I had this bug forever, i wonder if it's going to get fixed.

---

