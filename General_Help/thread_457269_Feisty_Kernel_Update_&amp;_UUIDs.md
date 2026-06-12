---
title: "Feisty Kernel Update &amp; UUIDs"
date: 2007-05-28
forum: General Help
---

### Post by drs305 on 2007-05-28
My computer had no problems with today's Feisty kernel update to 2.6.20-16 but apparently a lot of people did have problems.

My fstab is composed primarily of UUIDs, in particular my linux, home and windows partitions. I thought it was strange that Feisty had designated them as sdaX when they were on an IDE drive but they worked and I didn't care. Today I noticed that the kernel update had changed the two backup partitions that I had as sdaX and sdbX , which I use only for data storage. had been changed to hdaX and hdbX. They were unavailable until I changed the fstab settings to reflect the new designation.

Could some of today's problems be associated with people whose fstabs were written as /dev/sdaX until the update changed them to hdaX?

---

### Post by taurus on 2007-05-28
Yip.

---

