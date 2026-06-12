---
title: "G15 + lcdproc"
date: 2008-01-04
forum: General Help
---

### Post by dethredic on 2008-01-04
I would like to use ldproc with my G5 keyboard, but when I install it via synaptic or with the binary, using the ./configure --enable-drivers=all command it does not make the g15 driver (g15.so).

Does anyone know how I can fix this?

---

### Post by dethredic on 2008-01-04
Ok, I fixed this by doing a complete removal via synaptic.

Then I reinstalled via the binary. I did a LCDd -h to find the configuration file, then I opened that, searched for g15.so, and changed the directory in the LCDd.conf.

---

