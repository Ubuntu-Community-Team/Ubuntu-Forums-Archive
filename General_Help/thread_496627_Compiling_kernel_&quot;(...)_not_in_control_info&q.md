---
title: "Compiling kernel: &quot;(...) not in control info&quot;"
date: 2007-07-09
forum: General Help
---

### Post by Trebaruna on 2007-07-09
Not entirely sure where this question would best belong, but here goes:

I've followed the 'Master Kernel Thread' because I want some custom options (mostly highmem64g), but instead of using a vanilla source went with the ubuntu sources. The compiler starts doing its thing, but somewhere along the line it halts with an error:"package linux-image-2.6.20.3-ubuntu1k8-custom not in control info".

Some stuff around it:
```
install -p    -m 644 ./debian/templates.master /usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1k8-custom/DEBIAN/templates
dpkg-gencontrol -DArchitecture=i386 -isp         \
                        -plinux-image-2.6.20.3-ubuntu1k8-custom -P/usr/src/linux/debian/linux-image-2.6.20.3-ubuntu1k8-custom/
dpkg-gencontrol: error: package linux-image-2.6.20.3-ubuntu1k8-custom not in control info
make[1]: *** [debian/linux-image-2.6.20.3-ubuntu1k8-custom] Error 255
make[1]: Leaving directory `/usr/src/linux-source-2.6.20-2.6.20'
make: *** [binary/linux-image-2.6.20.3-ubuntu1k8-custom] Error 2
```

I know there are different methods available for compiling kernels, but there has to be a (fairly) easy fix. When I used the vanilla kernel all went well, so I can't be doing too much wrong...?

---

