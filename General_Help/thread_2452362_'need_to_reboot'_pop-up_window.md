---
title: "'need to reboot' pop-up window"
date: 2020-10-21
forum: General Help
---

### Post by marchello_lippi2 on 2020-10-21
Hi, 
How do I turn off 'need to reboot' pop-up window that appears from time to time after installing updates?

Lubuntu 

20.04.1 LTS

---

### Post by CelticWarrior on 2020-10-21
Rebooting is the way.

---

### Post by guiverc on 2020-10-21
The notifier I believe you're talking about is  (from a `ps -elf |grep update` on my own system)

```
0 S guiverc    74854       1  0  80   0 -   649 do_wai Oct17 ?        00:00:00 /bin/sh /usr/libexec/lubuntu-update-notifier/lubuntu-upg-notifier.sh
```

found in package `lubuntu-update-notifier`

Program details can be found at [https://phab.lubuntu.me/source/lubuntu-update-notifier/](https://phab.lubuntu.me/source/lubuntu-update-notifier/)

You can disable it in ***LXQt Session Settings***

See [https://manual.lubuntu.me/stable/3/3.2/3.2.13/session_settings.html](https://manual.lubuntu.me/stable/3/3.2/3.2.13/session_settings.html) in the Lubuntu manual for a *howto*, but you'll find it in the **Autostart** tab, just remove the "X" that tells it to autostart (*X is how it appears on my own themed system**, it may appear differently if you're using a different theme to me*).

---

### Post by marchello_lippi2 on 2020-10-21
**guiverc**,

Found lubuntu-upg-notifier.sh in LXQt Session Settings and disabled it. Thanks!

---

