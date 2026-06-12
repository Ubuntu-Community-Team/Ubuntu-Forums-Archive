---
title: "update manager hangs while installing linux-headers-3.8.0-42-generic"
date: 2014-07-06
forum: General Help
---

### Post by edwardsah3 on 2014-07-06
I'm running precise (12.04) on an amd FX-4100 quad-core processor. In the update manger window, the last information is

Preparing installation of linux-headers-3.8.0-42-generic

Under ps -ax | grep apt I get

29272 ?        SNl    0:02 /usr/bin/python /usr/sbin/aptd
29297 pts/2    SNs+   0:00 /usr/bin/python /usr/sbin/aptd
29370 pts/3    SNs+   0:05 /usr/bin/dpkg --status-fd 74 --unpack --auto-deconfigure /var/cache/apt/archives/linux-image-3.8.0-42-generic_3.8.0-42.63~precise1_amd64.deb /var/cache/apt/archives/linux-headers-3.8.0-42_3.8.0-42.63~precise1_all.deb /var/cache/apt/archives/linux-headers-3.8.0-42-generic_3.8.0-42.63~precise1_amd64.deb /var/cache/apt/archives/linux-libc-dev_3.2.0-65.99_amd64.deb

Any insight would be appreciated

---

### Post by ibjsb4 on 2014-07-06
Just hangs? No error message?

What does your boot directory look like?
```
ls /boot
```

---

