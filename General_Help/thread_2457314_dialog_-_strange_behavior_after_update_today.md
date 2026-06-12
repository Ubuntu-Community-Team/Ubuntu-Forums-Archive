---
title: "dialog - strange behavior after update today"
date: 2021-01-30
forum: General Help
---

### Post by ulrichmuc2 on 2021-01-30
My system:
 18.04.5 LTS, Kernel Linux 5.4.0-65-generic x86_64 Mate 1.22.2

After running the suggested update today, Jan 30, the program "dialog" shows a strange behavior:
The borders are drawn with letters instead of graphical characters. I attach a screenshot.

Btw: is there an easy way to find out which programs or libs have been changed by the last update?

---

### Post by Impavidus on 2021-01-30
You can take a look at the log files. /var/log/dpkg.log shows the upgraded packages.

About your issue, I don't know. It looks like an encoding mixup.

---

### Post by T6&amp;sfpER35% on 2021-01-30
if it was me ,i'd do a timeshift back , and update again. maybe something went haywire during update ...

---

### Post by ulrichmuc2 on 2021-01-30
mysteriously the odd behavior vanished by itself after a while. Very strange.

---

