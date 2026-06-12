---
title: "Fonts in screenlets are ugly"
date: 2008-05-25
forum: General Help
---

### Post by deltaromeo on 2008-05-25
Hi, I installed screenlets today and tried adding a few but the fonts all look pretty ugly!  I have smoothing and hinting enabled and don't have problems in other apps.  Hoping someone can help - I have attached a screenshot attached with 3 screenlets.

---

### Post by kerry_s on 2008-05-25
first step, disable bitmap fonts->
sudo dpkg-reconfigure fontconfig-config

say no to bitmaps.

reboot, to use the new font setup.

next, if there still bad, look at the manpages, most things have a setting for fonts that you can use in the command or in Xresources/Xdefaults file.

---

