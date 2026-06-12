---
title: "tasksel, purge, and remove"
date: 2013-08-09
forum: General Help
---

### Post by SchnappiJedi on 2013-08-09
Hi,

When using tasksel to remove a LAMP server, samba server, or anything else is using tasksel the same as using "purge," "remove" or both?

Thanks.

---

### Post by slickymaster on 2013-08-09
Don't use tasksel to remove packages, bad things can happen as it may remove many packages that it shouldn't, which can leave the machine in an inconsistent state. To remove something that you installed with tasksel, you need to mention the packages specifically.
See this: [Bug #574287]("https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/574287")

---

### Post by SchnappiJedi on 2013-08-09
> **slickymaster said:**
> Don't use tasksel to remove packages, bad things can happen as it may remove many packages that it shouldn't, which can leave the machine in an inconsistent state. To remove something that you installed with tasksel, you need to mention the packages specifically.
See this: [Bug #574287]("https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/574287")

Thank you for the information. Could someone still clarify however if tasksel theoretically does a remove, purge, or both?

---

