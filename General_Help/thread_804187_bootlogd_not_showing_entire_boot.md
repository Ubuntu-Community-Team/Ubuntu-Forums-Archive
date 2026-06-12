---
title: "bootlogd not showing entire boot"
date: 2008-05-22
forum: General Help
---

### Post by mockingbird on 2008-05-22
I'm trying to use bootlogd enabled but I'm not getting a whole lot of information.

I've already got "BOOTLOGD_ENABLE" set to Yes in /etc/default/bootlogd, but I'm only getting a fraction of the boot info.

I've tried manually changing the number prefix in rc0.d to a higher number for bootlogd so it should start earlier in the boot process.  I've also tried using "update-rc.d -f bootlogd remove" and then "update rc.d bootlogd defaults x(tried as high as 2)".

All this to no avail.  Now I'm even getting less info than before.

Help!!!

I'm using Debian 4.0r3 not that it makes a difference.

---

