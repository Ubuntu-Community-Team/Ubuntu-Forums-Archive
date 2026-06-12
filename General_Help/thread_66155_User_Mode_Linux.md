---
title: "User Mode Linux"
date: 2005-09-16
forum: General Help
---

### Post by shmk on 2005-09-16
I tried to install UML on my Ubuntu 2.6.10-5-386 but I failed a lot of times...

I have used 2 kind of kernel-sources:
- 2.6.10 from Ubuntu repository
- 2.6.10 from [www.kernel.org](www.kernel.org)

As config I used xconfig and for configuration file I used the defconf in ./kernel-src/arch/um/defconf coping it on the ./kernel-src folder with name .config

I made the ./linux and ./vmlinux but when I try to boot the uml machine it always crash.

My root_fs is a Debian3.0r0.sarge.ext2 (i must use this, I cannot make another one)

The only uml ./linux file that works is the one that I make with configuration file as the uml "defconf" but **without module support**.

Please I need a hand  ](*,)

---

