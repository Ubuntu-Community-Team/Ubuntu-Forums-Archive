---
title: "Fonts are not anti-aliased in some applications"
date: 2006-10-09
forum: General Help
---

### Post by limitedmage on 2006-10-09
Hi,

On some applications (XMMS, Audacity, and some others) the fonts are rendered incorrectly and fuzzy. How can I correct this?

BTW, I'm using x86 Dapper.

A couple of screenshots are attached.

---

### Post by lawina on 2006-10-09
I have the same issue. Maybe this is universal.

---

### Post by rubinstein on 2006-10-09
These applications use the GTK 1.* toolkit which has no antialiasing.

I think the next version of audacity will use GTK 2.* (with wxwidgets) so this version should have nicer fonts.

---

