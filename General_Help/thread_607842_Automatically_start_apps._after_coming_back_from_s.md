---
title: "Automatically start apps. after coming back from suspend?"
date: 2007-11-09
forum: General Help
---

### Post by Greasyfingers on 2007-11-09
Is it possible to automatically start an application or run a script after coming back from suspend?

---

### Post by geirha on 2007-11-09
From what I can gather, when the computer resumes, the acpi daemon runs the scripts in /etc/acpi/resume.d/ , so adding your script there might work.

---

### Post by Greasyfingers on 2007-11-09
I think you're right, Geirha, but I'm clearly missing something. A simple script which starts an application doesn't work when I put it in resume.d.

Can anyone point to some guidelines as to what will and will not work in resume.d?

---

