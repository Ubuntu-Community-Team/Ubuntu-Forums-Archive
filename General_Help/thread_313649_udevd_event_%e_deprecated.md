---
title: "udevd event %e deprecated"
date: 2006-12-06
forum: General Help
---

### Post by wildfox on 2006-12-06
Hi!
I get this warning on every boot:
udevd-event[3376] find_free_number: %e is deprecated and will be removed Don't use it.
So I guess i have to remove the %e from rules.. or from where? Where can i find this?

Thx,
 wildfox

---

### Post by wildfox on 2007-01-27
Fixed.
It was in /etc/udev/rules.d/11-hplj10xx.rules
I removed the '%e', no more warning, everyone's happy.

---

