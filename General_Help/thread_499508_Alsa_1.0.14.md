---
title: "Alsa 1.0.14"
date: 2007-07-12
forum: General Help
---

### Post by spclk on 2007-07-12
I'm having trouble installing new ALSA drivers for 7.04 installation. I did the./configure for the driver one fine but I'm having trouble with the plugins (it seems that ALSA changed LIB to plugins). I start the ./configure but towards the end it says "No package 'alsa' found"

Any ideas? ](*,)

---

### Post by geraldm on 2007-07-13
after installing alsa drivers, you need to either: 1) reboot or 2) (execute as root) ldconfig
This flushes the old cache, which did not have the alsa package.

Note also that there are two separate packages alsa-lib-1.0.14a.tar.bz2 alsa-plugins-1.0.14.tar.bz2

---

### Post by spclk on 2007-07-13
Ok I'll try that. Thanks.

---

