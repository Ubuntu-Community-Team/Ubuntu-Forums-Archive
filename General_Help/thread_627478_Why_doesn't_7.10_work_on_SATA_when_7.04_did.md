---
title: "Why doesn't 7.10 work on SATA when 7.04 did?"
date: 2007-11-30
forum: General Help
---

### Post by syarost on 2007-11-30
Wubi 7.04 worked the first time with no issues on my Inspiron 1705 running Windows XP SP2, Core 2 Duo 7400, NVIDIA 7900 GS, and Travelstar 7K200 200GB.  Why won't 7.10 Work???  Can you fix it?

---

### Post by ago on 2007-11-30
It's an issue with the kernel used in 7.10 and it's not trivial to fix

---

### Post by daspooky on 2007-12-02
Does that mean a normal Gutsy install (without wubi) also suffers these issues (freezes)? Or is the problem only present when combining wubi and the kernel used in Gutsy?

---

### Post by ago on 2007-12-03
It's a problem with loopmounted files, which is most common for wubi

---

