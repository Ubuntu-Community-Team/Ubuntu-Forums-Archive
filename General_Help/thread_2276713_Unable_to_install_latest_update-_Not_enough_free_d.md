---
title: "Unable to install latest update- Not enough free disk space on /boot"
date: 2015-05-04
forum: General Help
---

### Post by konrad6 on 2015-05-04
For the past few days, I've been getting an update notice for my Ubuntu 14.04 x64 system.

When I click to install it, I get this message:

> 
Not enough free disk space

The upgrade needs a total of 84,0M free space on disk /boot. Please free an additional 22,5 M on /boot. Empty your trash and remove temporary packages of former installations using "sudo apt-get clean"

According to Gparted, my primary partition contains 232 GiB, and my /boot has 243 MiB, 70,78 MiB unused. My primary is encrypted, so I believe that means that I can't resize it and allocate the free space to /boot, Gparted prevented me at least.

What should I do with this?

---

### Post by Mark Phelps on 2015-05-04
The info in the link says resizing can be done -- but it is difficult: [https://help.ubuntu.com/community/ResizeEncryptedPartitions]("https://help.ubuntu.com/community/ResizeEncryptedPartitions")

---

