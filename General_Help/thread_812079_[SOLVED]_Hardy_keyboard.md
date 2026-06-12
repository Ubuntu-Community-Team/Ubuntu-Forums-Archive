---
title: "[SOLVED] Hardy keyboard"
date: 2008-05-29
forum: General Help
---

### Post by jonnieH on 2008-05-29
Odd keyboard behaviour since upgrading to Hardy - After the upgrade the default keyboard changed to US (Mine is UK) so I went to preferences/keyboard and altered the default to UK - all appeared to be OK with the right characters displayed on typing. Since re-booting, the default (and only) keyboard listed is UK but the characters typed are US ! 

Any thoughts anyone?

---

### Post by twright on 2008-05-29
you could try editing /etc/X11/xorg.conf (gksu gedit /etc/X11/xorg.conf) and changing keyboard from us to gb

---

