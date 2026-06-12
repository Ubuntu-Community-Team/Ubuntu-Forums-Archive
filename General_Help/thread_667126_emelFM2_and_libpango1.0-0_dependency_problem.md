---
title: "emelFM2 and libpango1.0-0 dependency problem"
date: 2008-01-14
forum: General Help
---

### Post by Steffen_77 on 2008-01-14
When I try to install emelFM2 I get the following dependency error:

sudo dpkg -i /home/steffen/Desktop/emelfm2_0.3.6-1_i386.deb 
Selecting previously deselected package emelfm2.
(Reading database ... 121210 files and directories currently installed.)
Unpacking emelfm2 (from .../emelfm2_0.3.6-1_i386.deb) ...
dpkg: dependency problems prevent configuration of emelfm2:
 emelfm2 depends on libpango1.0-0 (>= 1.18.3); however:
  Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
dpkg: error processing emelfm2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emelfm2

Any idea how to fix this?

-Steffen-

---

### Post by erpo on 2008-01-14
```
emelfm2 depends on libpango1.0-0 (>= 1.18.3); however:
Version of libpango1.0-0 on system is 1.18.2-0ubuntu1.
```

This part makes it clear what is happening. Your libpango1.0-0 is too old for your emelfm2. Or, you could also say that your emelfm2 is too new for your libpango1.0-0.

You need to install a newer version of libpango or an older version of emelfm2.

---

### Post by Steffen_77 on 2008-01-14
> **erpo said:**
> You need to install a newer version of libpango or an older version of emelfm2.

Sure, makes sense. But where do I get a newer version of libpango from?

---

### Post by Seisen on 2008-01-14
You can download it from here but you will need to compile it

[http://ftp.gnome.org/pub/GNOME/sources/pango/]("http://ftp.gnome.org/pub/GNOME/sources/pango/")

---

### Post by Steffen_77 on 2008-01-14
> **Seisen said:**
> You can download it from here but you will need to compile it

Or follow this advice: [http://ubuntuforums.org/showthread.php?t=616774]("http://ubuntuforums.org/showthread.php?t=616774")

---

