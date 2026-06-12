---
title: "Third party deb file install bug persisting in 16.04.1?"
date: 2016-07-22
forum: General Help
---

### Post by brian113 on 2016-07-22
I have a brand new, clean install of 16.04.1 downloaded directly from Ubuntu. Went to install Google Chrome using the .deb downloaded from their website and, lo and behold, the bug where the Software Center refuses to install third party debian files and locks up dpkg rears its ugly head. I thought this was already fixed?

---

### Post by howefield on 2016-07-23
Should be as far as I can tell, what version of gnome-software do you have ?

The fix was released with gnome-software (3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1) xenial.

A freshly installed and updated 16.04.1 should have the more current.. 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1

FWIW, you can install local deb files with apt as of 16.04.

```
sudo apt install path/to/deb
```

---

