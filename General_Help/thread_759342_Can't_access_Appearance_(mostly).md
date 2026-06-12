---
title: "Can't access Appearance (mostly)?"
date: 2008-04-19
forum: General Help
---

### Post by harryeddy on 2008-04-19
Hi, I enjoy computers but am fairly new to Linux. I'm running Ubuntu 7.10 (Gutsy) on an Intel 2nd Gen MacBook.
I was using the package manager to clean out some stuff and probably uninstalled something I shouldn't have:(
Anyway, my Appearance preference panel will only select different themes. When I try to customize the themes or add new ones, it simply shows a dialog with nothing in it but a few shapes showing where the controls should be. Also, I cannot click on any other tab in Appearance.
Thanks in Advance (I'm really enjoying Ubuntu so far:))

---

### Post by marufaberlin on 2008-04-19
try ```
apt-get -f install
```
or ```
apt-get -f install ubuntu-desktop
```. remove ubuntu-desktop first if you need to. All your customization wll get lost.

---

