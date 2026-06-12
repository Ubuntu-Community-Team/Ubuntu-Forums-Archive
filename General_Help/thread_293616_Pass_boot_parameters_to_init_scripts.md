---
title: "Pass boot parameters to init scripts?"
date: 2006-11-05
forum: General Help
---

### Post by Rob_H on 2006-11-05
How do you pass boot parameters as environment variables to init scripts in Edgy? This worked without a problem in Dapper. Apparently, Upstart handles this differently...?

---

### Post by squido on 2006-12-06
Cheesy, but you can parse /proc/cmdline.

---

