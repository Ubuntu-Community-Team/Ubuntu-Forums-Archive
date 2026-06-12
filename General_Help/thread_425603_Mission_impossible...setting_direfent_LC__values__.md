---
title: "Mission impossible...setting direfent LC_* values  than default locale."
date: 2007-04-27
forum: General Help
---

### Post by revertex on 2007-04-27
I've searched in these forums and other places around, but it seems that nobody already found a solution or knows how to solve it.

I want to set diferent LC values than default lang env but i can't found the proper documentation, if exist, to how to do it.

Actually, my locale output is

```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

but i want to change to:
```
LANG=en_US.UTF-8
LC_CTYPE="pt_BR.UTF-8"
LC_NUMERIC="pt_BR.UTF-8"
LC_TIME="pt_BR.UTF-8"
LC_COLLATE="pt_BR.UTF-8"
LC_MONETARY="pt_BR.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="pt_BR.UTF-8"
LC_NAME="pt_BR.UTF-8"
LC_ADDRESS="pt_BR.UTF-8"
LC_TELEPHONE="pt_BR.UTF-8"
LC_MEASUREMENT="pt_BR.UTF-8"
LC_IDENTIFICATION="pt_BR.UTF-8"
```

i changed /etc/einviroment, /etc/defalut/locale and run dpkg-reconfigure -p low localeconf, but no avail, nothing was changed.

I'm not sure if i'm doing something wrong or it's really a bug.

Even in gentoo it's dead simple, in my old gentoo install i just changed, /etc/env.d/00locale and it's done.
 Why it's so hard in a distro that is supose to be friendly?

---

### Post by zvacet on 2007-04-27
Look in** system>administration>language suport**

---

### Post by revertex on 2007-04-27
> **zvacet said:**
> Look in** system>administration>language suport**

Thanks, but this only work if i'm using gnome, i want to set system wide, for all users and all window managers

---

