---
title: "Kernel update: is this odd?"
date: 2014-08-29
forum: General Help
---

### Post by vasa1 on 2014-08-29
I use apt-get dist-upgrade routinely. Today I got a kernel update and saw this:```
...
done
Setting up linux-image-generic (3.13.0.35.42) ...
Setting up linux-headers-3.13.0-35 (3.13.0-35.62) ...
Setting up linux-headers-3.13.0-35-generic (3.13.0-35.62) ...
Setting up linux-headers-generic (3.13.0.35.42) ...
Setting up linux-generic (3.13.0.35.42) ...
[07:11 AM] ~ $ 
```Why are there 3.13.0.35.42 and 3.13.0-35.62? Did anyone see the same thing? Is it normal and just that I noticed it for the first time?

---

### Post by mikewhatever on 2014-08-29
Don't see why not. The meta-packages (linux-generic, linux-image-generic) are 3.13.0.35.42, while the rest (image and headers) are 3.13.0-35.62.

...here's what it looks like on 12.04:
> 
ii  linux-headers-3.2.0-67                 3.2.0-67.101                            Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic         3.2.0-67.101                            Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic                  3.2.0.67.79                             Generic Linux kernel headers
ii  linux-image-3.2.0-67-generic           3.2.0-67.101                            Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.67.79                             Generic Linux kernel image


---

