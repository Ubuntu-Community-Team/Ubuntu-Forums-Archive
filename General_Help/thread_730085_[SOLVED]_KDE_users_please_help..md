---
title: "[SOLVED] KDE users please help."
date: 2008-03-20
forum: General Help
---

### Post by Bruce M. on 2008-03-20
I need to know the location of a file in a KDE setup.

The default test editor - kate

GNOME & gedit
/usr/bin/gedit

Xfce & mousepad
/usr/bin/mousepad

I am assuming that kate would be the same:

KDE & kate
/usr/bin/kate

Is this correct?

Thanks
Bruce

---

### Post by OffAxis on 2008-03-20
yes, and here's all my instances of 'kate' in case you need them.

```

sudo find -name kate
./home/<username>/.kde/share/apps/kate
./usr/bin/kate
./usr/lib/mime/packages/kate
./usr/share/lintian/overrides/kate
./usr/share/doc/kde/HTML/en/kate
./usr/share/doc/kate
./usr/share/apps/kate
./usr/share/menu/kate

```

---

### Post by Bruce M. on 2008-03-20
> **OffAxis said:**
> yes, and here's all my instances of 'kate' in case you need them.

**[CENTER]Thank you kindly OffAxis[/CENTER]**

---

### Post by OffAxis on 2008-03-20
you're most welcome.

---

