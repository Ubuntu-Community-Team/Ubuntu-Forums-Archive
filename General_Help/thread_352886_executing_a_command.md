---
title: "executing a command"
date: 2007-02-03
forum: General Help
---

### Post by hovnatan on 2007-02-03
Hi

How can I execute some command after resuming the computer from suspend-to-ram in Ubuntu? I am using just default power management tools.

Thanks,
Hovo

---

### Post by gradedcheese on 2007-02-04
Hi.  I believe the resume scripts live in:

/etc/acpi/resume.d/

(basically, /etc/acpi/resume.sh runs each file in that directory)

---

