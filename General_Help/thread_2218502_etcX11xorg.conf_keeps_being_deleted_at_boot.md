---
title: "/etc/X11/xorg.conf keeps being deleted at boot"
date: 2014-04-20
forum: General Help
---

### Post by gtozzi on 2014-04-20
Hi there!

I've just **upgraded** to 14.04 and now every time i (re)boot my system, **/etc/X11/xorg.conf** is renamed as /etc/X11/xorg.conf.backup.

Every time I have I put the file back in place from backup and every time it disappears again.

Is there anything new I'm missing? Any way to stop Ubuntu to self-vandalize?

Thank you everybody

---

### Post by troy.mcclure on 2014-04-22
Same problem here. Helpless. Also OpenCL not recognizing all cards but one. Tried latest AMD beta drivers and fglrx-updates.

---

### Post by troy.mcclure on 2014-04-23
workaround: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1310489](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1310489)

---

### Post by gtozzi on 2014-04-23
Thank you very much, it could've took me days to find it.

Ubuntu "smart" boot process has always been a pain, but now deleting config files is really too much... I just want an OS that obeys my orders, if I wanted a "smart" guessing OS, I wouldn't use GNU/Linux -.-

---

