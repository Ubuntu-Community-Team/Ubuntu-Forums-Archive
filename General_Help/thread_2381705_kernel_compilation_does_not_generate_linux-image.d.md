---
title: "kernel compilation does not generate linux-image*.deb"
date: 2018-01-04
forum: General Help
---

### Post by tomadore2 on 2018-01-04
I tried to build my own Ubuntu kernel because I wanted to configure it such that it disables xhdc (USB 3.0) support. I followed the instructions on [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel).
However, the final build phase (*fakeroot debian/rules binary-headers binary-generic*) seems to build only these Debian packages:
```
linux-cloud-tools-4.4.0-103_4.4.0-103.126+custom_amd64.deb
linux-headers-4.4.0-103_4.4.0-103.126+custom_all.deb
linux-tools-4.4.0-103_4.4.0-103.126+custom_amd64.deb
```

I wonder why there is no linux-image-...deb package. Does anybody know why there is none? I already tried to checkout a few other branches (other than master) but linux-image* Debian packages are not built either.

I have uploaded the console output in here: [ATTACH]278042[/ATTACH]

---

### Post by Xian on 2018-01-04
What directory are you searching for the kernel image? 

From your console output:

```
INSTALL_DIR="/media/Data/Downloads/ubuntu-xenial/debian/linux-image-4.4.0-103-generic"
```

---

### Post by tomadore2 on 2018-01-05
I was looking in [COLOR=#000000][FONT=&quot]/media/Data/Downloads[/FONT][/COLOR] (one folder up to where it has been compiled). I also checked in *INSTALL_DIR="/media/Data/Downloads/ubuntu-xenial/debian/linux-image-4.4.0-103-generic *but there was no Debian package inside. Anyway, it actually generates the linux-image-... Debian package now if I follow this guide: [https://www.maketecheasier.com/build-custom-kernel-ubuntu/](https://www.maketecheasier.com/build-custom-kernel-ubuntu/)

---

