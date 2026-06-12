---
title: "fingerprint-gui says &quot;No Devices Found!&quot;"
date: 2017-08-08
forum: General Help
---

### Post by steamer360 on 2017-08-08
Has anyone managed to get fingerprint-gui to work with an Asus UX430? The scanner model is Elantech if that helps: ```
Elan Microelectronics Corp. (0x4f3) unknown device (0x903)
```

For some reason it notices the scanner but registers it as "unknown device".

Thanks for the help in advance.

---

### Post by steamer360 on 2017-08-09
Bump

---

### Post by steamer360 on 2017-08-30
Bump

---

### Post by #&amp;thj^% on 2017-08-30
This is not good news but have a look: [https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/1641290](https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/1641290)
> This bug should actually be a feature request. There is currently no support for elantech fingerprint scanners in libfprint. Someone needs to write a driver for it. It's proprietary, so that might be tricky.

---

