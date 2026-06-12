---
title: "[SOLVED] Where is Preferences &amp;gt; Hardware Information?"
date: 2008-05-29
forum: General Help
---

### Post by kmclar on 2008-05-29
Hi all,

I have a fresh install of Hardy 8.04 (i386).  I have seen references in the forum to using System>Preferences>Hardware Information, but I do not have this.  Is there something I need to install?

Thanks!

---

### Post by LaRoza on 2008-05-29
> **kmclar said:**
> Hi all,

I have a fresh install of Hardy 8.04 (i386).  I have seen references in the forum to using System>Preferences>Hardware Information, but I do not have this.  Is there something I need to install?

Thanks!
Could it be under "Administration"?

---

### Post by kmclar on 2008-05-29
No, It's not under any of the menus, and I don't see it in the list under Add/Remove either.

---

### Post by Pi rules on 2008-05-29
Hello :)

The program you are referring to, hal-device-manager, isn't included in Hardy Heron.  Try gnome-device manager instead to see if it is a suitable replacement.

1.  Open a terminal (Applications -> Accessories -> Terminal)
2.  Type the following and press Enter: **sudo apt-get install gnome-device-manager**
3.  It may mention needing one or more extra packages (see [this](http://packages.ubuntu.com/hardy/gnome/gnome-device-manager) for a list of the packages on which it depends).  Type **y** and press Enter again if you are prompted to continue.

When it finishes, you can launch it by going to Application -> System Tools -> Device Manager or by typing **gnome-device-manager** in the Terminal.

---

### Post by noynac on 2008-05-29
---

---

### Post by kmclar on 2008-05-29
Thanks Pi Rules!  That was it!

---

### Post by Pi rules on 2008-05-30
You're welcome. :)

---

### Post by alvinator@ on 2009-07-30
<-- wrong post -->

---

