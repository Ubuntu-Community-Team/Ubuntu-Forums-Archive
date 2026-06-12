---
title: "Hangs on boot"
date: 2023-01-13
forum: General Help
---

### Post by AllanP on 2023-01-13
Hangs on boot after displaying: [         3.638379] blacklist: Problem blacklisting hash (-13)
                                                   [         3.639636] blacklist: Problem blacklisting hash (-13)
It has always shown those lines plus a couple more but has continued to boot. Now it hangs there.

---

### Post by yancek on 2023-01-13
The link below indicates the problem can be solved by first backing up then clearing secure boot keys.

[https://forum.archlabslinux.com/t/blacklist-problem-blacklisting-hash-13-errors-on-boot/6674](https://forum.archlabslinux.com/t/blacklist-problem-blacklisting-hash-13-errors-on-boot/6674)

---

### Post by AllanP on 2023-01-13
It has worked fine up until today; always showing the blacklist lines, but carrying on to boot. I was able to get in using another boot option and tried to do a Timeshift restore, but that crashed on me. I don't have secure boot enabled. I'll restore an earlier image with Acronis.

---

