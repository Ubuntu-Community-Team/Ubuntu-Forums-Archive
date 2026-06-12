---
title: "[SOLVED] Please I need Ubuntu 7.10 kernel's .config file"
date: 2008-02-21
forum: General Help
---

### Post by HanDy_man on 2008-02-21
Where can I get standart Ubuntu 7.10 .config file (the file you get after make oldconfig in kernel source directory)? I've upgrade kernel to 2.6.24.2 and when I type make oldconfig, .config is different than before. I've try to boot with the old kernel (2.6.22-14-generic) but it's same.

---

### Post by blazercist on 2008-02-21
use make menuconfig instead of oldconfig and just load the .config file from one of the standard ubuntu kernels...

---

### Post by HanDy_man on 2008-02-21
Yes it works. Thanks for the fast response.

---

