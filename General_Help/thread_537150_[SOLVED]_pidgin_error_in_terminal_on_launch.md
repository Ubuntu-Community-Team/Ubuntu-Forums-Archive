---
title: "[SOLVED] pidgin error in terminal on launch"
date: 2007-08-28
forum: General Help
---

### Post by Bethrine on 2007-08-28
Pidgin launches from the terminal fine, but I get this error in the terminal...

(pidgin:20780): Pango-WARNING **: Error loading GPOS table 4097

???

---

### Post by apetresc on 2007-08-28
> **Bethrine said:**
> Pidgin launches from the terminal fine, but I get this error in the terminal...

(pidgin:20780): Pango-WARNING **: Error loading GPOS table 4097

???

It's not an error, just a warning. It's completely intentional. The font manager writes a table that is empty in Linux (it is only used by Windows). Pango warns about this, but it does not actually affect normal operation in any way, it is intentional.

---

### Post by Bethrine on 2007-08-28
Thanks!

---

