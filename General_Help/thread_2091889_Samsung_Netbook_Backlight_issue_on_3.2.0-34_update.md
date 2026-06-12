---
title: "Samsung Netbook Backlight issue on 3.2.0-34 update"
date: 2012-12-06
forum: General Help
---

### Post by gescom on 2012-12-06
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1086921](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1086921)

Just updated Xubuntu 12.04 lts tonight and lost control of the my Samsung N150 plus netbook backlight/brightness control. It was working perfectly but the new 3.2.0-34 kernel seems to be the problem. Anyone else with this issue? Hope it gets resolved soon.

Otherwise couldn't be happier with Xubuntu. It's a great distro. :)

---

### Post by 2F4U on 2012-12-06
I had a similar problem on a Acer notebook and was able to solve it by adding

acpi_osi=Linux acpi_backlight=vendor

to the grub kernel line.

---

### Post by gescom on 2013-01-03
Thank you so much 2F4U! That kernel line got the backlight control working again. :)

---

