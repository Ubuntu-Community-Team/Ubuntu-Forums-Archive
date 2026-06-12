---
title: "Disable No. Days HD Boot Scan"
date: 2008-04-07
forum: General Help
---

### Post by mikeym on 2008-04-07
Hi,

Is there any way to tell my laptop - which has a knackered internal battery to ignore the number of days when deciding whether to scan my hard disk or not?

It always defaults to 1904 which is not great but as soon as I'm in and online the date and time are automatically corrected.

---

### Post by chunchengch on 2008-04-07
I suppose that you want to disable the check of hard disk, if so, this command will be helpful

[COLOR="Red"]$ sudo tune2fs -c 0 /dev/sdax[/COLOR]

x is the partition number

---

