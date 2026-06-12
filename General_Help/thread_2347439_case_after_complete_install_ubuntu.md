---
title: "case after complete install ubuntu"
date: 2016-12-25
forum: General Help
---

### Post by mosab99 on 2016-12-25
i install ubuntu yesterday , and after complete install i update it
so, i restart my pc to complete update 
I do all that , but after i restart my pc i got this masseges 
[   3.426125] sd 0:0:0:0 [sdb] no caching mode page found 
[   3.426130] sd 0:0:0:0 [sdb] assaming driver cacher : write through 
/dev/sda1:clean ,223828/19406848 files , 241311/7762036 blocks

---

### Post by ian-weisser on 2016-12-25
> **mosab99 said:**
> [   3.426125] sd 0:0:0:0 [sdb] no caching mode page found 
[   3.426130] sd 0:0:0:0 [sdb] assaming driver cacher : write through
 
The Linux kernel queried your hardware. The second storage device found (sdb) lacked or refused to admit some expected features.The kernel shrugged, noted the discrepancy, and continued. Sometimes a false positive.

Usually not a fatal error. If your system runs unusually slowly, that might be a possible cause.
How to fix: When the device wears out, replace it with something more compatible. 

> **mosab99 said:**
> /dev/sda1:clean ,223828/19406848 files , 241311/7762036 blocks

Not an error. Just a status message that the filesystem you are about to mount on sda1 had been checked and is clean.

---

