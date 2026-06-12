---
title: "skype camera reversed"
date: 2013-02-24
forum: General Help
---

### Post by walkmanlu on 2013-02-24
Hi,

when I'm using Skype them my camera is reversed. I use a Asus Laptop X52F and Ubuntu 12.04 LTS.
All recommendations found here did not resolve the problem.

Who can help me to fix this issue?

Nany thanks in advance.

walkman vrom luxemburg

---

### Post by matt_symes on 2013-02-24
Hi

Does this help ?

[http://pc-freak.net/blog/how-to-fix-upside-down-inverted-web-camera-laptop-asus-k51ac-issue-on-ubuntu-linux-and-debian-gnu-linux/](http://pc-freak.net/blog/how-to-fix-upside-down-inverted-web-camera-laptop-asus-k51ac-issue-on-ubuntu-linux-and-debian-gnu-linux/)

Kind regards

---

### Post by walkmanlu on 2013-02-24
when I execute this command:
apt-get --yes install libv4-0

it tells me that the package libv4-0 can't be found

---

### Post by xc3RnbFO8P on 2013-02-26
Try from terminal:
> export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

---

