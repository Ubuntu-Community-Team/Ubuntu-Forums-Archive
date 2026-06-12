---
title: "Scripts in /etc/acpi/resume.d aren't executed."
date: 2007-07-05
forum: General Help
---

### Post by jazzgossen on 2007-07-05
It seems that none of the scripts in /etc/acpi/resume.d/ are executed when I resume from hibernation. What could cause this? How could I start troubleshooting? I'm using uswsusp.

---

### Post by laklare on 2007-11-20
I have this problem in Ubuntu 7.10. Is uswsusp supposed to run the /etc/acpi/resume.d scripts? If not, is there some other way to make it run a script when in resumes from suspend?

---

### Post by jazzgossen on 2007-11-20
I don't know. Since 7.10, I started using the standard suspend mechanism instead, and now the resume.d scripts work again.

---

