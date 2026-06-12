---
title: "Gutsy broke my keyboard settings"
date: 2007-10-20
forum: General Help
---

### Post by robinl on 2007-10-20
After upgrading to gutsy from feisty back when it was still beta, I started getting ´ instead of ' for quotation marks, typing ´ + e doesn´t produce é anymore (even though my keyboard is set to US-intl) and I can´t activate SCIM anymore. I´ve installed scim-qtimm per [http://ubuntuforums.org/showthread.php?t=461421](http://ubuntuforums.org/showthread.php?t=461421) but not it just sits in my system tray and does nothing when I left-click on it or press ctrl-space. Does anyone know how to fix this?

---

### Post by robinl on 2007-10-20
Ok after looking at the keymap layout for US-intl it seems they changed it in Gutsy to the current layout. Still, dead key doesn´t work at all, or did they change that is well?

---

### Post by jenhsun on 2007-10-23
[https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

---

### Post by robinl on 2007-10-28
Actually it's [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/34282](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/34282), and I've found a way around it, described there.

---

### Post by jenhsun on 2007-10-28
> **robinl said:**
> Actually it's [https://bugs.launchpad.net/ubuntu/+source/scim/+bug/34282](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/34282), and I've found a way around it, described there.

Thanks. That's great.
I think I got a terrible mistake for not take a look at the scim doc.

---

