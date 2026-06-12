---
title: "How to read xorger version number 1:7.7+7?"
date: 2016-01-11
forum: General Help
---

### Post by cdoublejj on 2016-01-11
I need to know what version 1:7.7+7 is. My nvidia fx5200 driver needs version 1.15.

---

### Post by mc4man on 2016-01-11
look at the installed xserver-xorg-core package (or if using 14.04.2+ the xserver-xorg-core-lts-xxxxxxx package
basically - 
14.04/14.04.1 - 1.15
14.04.2/14.10 -  1.16
14.04.3/15.04/15.10 - 1.17

Or install inxi & run 
inxi -b
will be in Graphics: section

---

