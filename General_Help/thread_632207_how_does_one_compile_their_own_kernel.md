---
title: "how does one compile their own kernel"
date: 2007-12-05
forum: General Help
---

### Post by HokeyFry on 2007-12-05
just for kicks, i would like to compile my own kernel. does anyone know of any good guides or where i might get started?

---

### Post by jespdj on 2007-12-05
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Try Googling for "ubuntu compile kernel"

---

### Post by g2g591 on 2007-12-05
download the kernel source (extract it too), install ncurses-dev, cd into the directory where you extracted it, and type make defoptions then make menuconfig (select all the options you need, gentoo has some good advice on how to find them) then make then sudo make install, then you have your own custom compiled kernel installed into your /boot directory.

---

