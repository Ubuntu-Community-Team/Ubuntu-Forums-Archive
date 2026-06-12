---
title: "[SOLVED] GDM Theme Imports but will not apply"
date: 2007-11-11
forum: General Help
---

### Post by kd7swh on 2007-11-11
Theme is imported into GDMsetup I select it, but it isn't applied to the GDM login screen for some reason. Any ideas?


___

Its not just the theme, none of my changes in GDM are taking effect!

Help

---

### Post by kahosei on 2007-11-11
I have the same problem. What did you do to solve it?

---

### Post by kd7swh on 2007-11-11
Turns out I had deleted the file:
```
/etc/gdm/gdm.conf-custom
```

I just created a new blank document in that directory with that name, and it worked.

---

### Post by kahosei on 2007-11-11
It worked!

It's just so simple when you know what to do. :-)


I used some time on this issue, so thank very much you!

:D

---

