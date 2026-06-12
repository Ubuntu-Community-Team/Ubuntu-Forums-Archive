---
title: "libstdc++5 vs. libstdc++6"
date: 2007-10-03
forum: General Help
---

### Post by lognok on 2007-10-03
what's the difference between these two libraries?
  and
why do certain programs depend on for example libstdc++5 when libstdc++6 is installed?
  and
can I somehow tell the installer to use libstdc++6 instead of libstdc++5 or would that ruin everything?

Cause of questions?: when I tried to install Xilinx Webpack 9.2i, it's refused because I didn't have libstdc++5 installed. Had to install it, although libstdc++6 was already installed.

Just curious :)



Take care

---

### Post by por100pre1 on 2007-10-03
Maybe you'll find what you want [here]("http://gcc.gnu.org/libstdc++/"). BTW, you can have both libraries installed, no problems are to be expected.

---

### Post by lognok on 2007-10-04
Thanks por100pre1 for the link.

I gather that libsdtc++ is locked to the version of gcc that it's released with for good or bad. And packages are built for specific versions of gcc since they can't use newer gcc versions.

Well, thanks again.

---

