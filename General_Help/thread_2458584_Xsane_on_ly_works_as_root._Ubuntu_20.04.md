---
title: "Xsane on ly works as root. Ubuntu 20.04"
date: 2021-02-27
forum: General Help
---

### Post by trueabdrahim on 2021-02-27
Edit /etc/sans.d/ yourscanner.config. I mycase the last line was
#usb /dev/usb/scanner0.
So removing the "#" solved the problem. I can now scan as a normal user.

---

