---
title: "APM instead of ACPI, how?"
date: 2004-10-30
forum: General Help
---

### Post by Bob Collins on 2004-10-30
How do I uninstall ACPI and run APM instead?

I am trying to run Ubunto on an older Dell Latitude laptop (CPiA) which has a broken ACPI implementation. The laptop has worked with other distributions fine with APM as the power manager.

I tried to uninstall ACPI and install APM but the ACPI package is depended on by "ubuntu-desktop". This is bad. Does anyone have any ideas?

Looking at the planned changes for the spring release shows that they know of this problem. How do I fix it for now?

Thanks,

Bob Collins
Sunnyvale CA USA


*

---

### Post by jdong on 2004-10-30
don't "uninstall". Just boot with **acpi=off apm=on**. Use /boot/grub/menu.lst to make the changes permanent.

This is a duplicate of thread [http://ubuntuforums.org/showthread.php?p=8630#post8630](http://ubuntuforums.org/showthread.php?p=8630#post8630)

Please do not cross-post. it doesn't get you answers any faster.

---

