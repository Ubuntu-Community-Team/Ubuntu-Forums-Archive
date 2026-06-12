---
title: "Firestarter &amp; iptables problem!"
date: 2005-03-30
forum: General Help
---

### Post by CrustyDOD on 2005-03-30
Using Warty and i cannot install Firestarter, tried with packet manager and in console:

The following packages have unmet dependencies:
  firestarter: Depends: iptables (>= 1.2.11) but 1.2.9-10ubuntu0.1 is to be installed
E: Broken packages

What to do?

Yeah yeah, i was playing with Packet Manager and somehow i managed to remove firestarter from Ubuntu... Don't ask!

---

### Post by soul_rebel on 2005-03-31
look if there is another OLDER version of firestarter, which perhaps is on warty cd...

---

### Post by A-star on 2005-03-31
[QUOTE=soul_rebel]look if there is another OLDER version of firestarter, which perhaps is on warty cd...[/QUOTE]
 In synaptic do a CTRL-E on the firestarter package on choose the 0.9.7 version.

---

### Post by farnsworth on 2005-04-03
As an alternative to using an older version, I usually just:
```

sudo dpkg -i --ignore-depends=somelib1.23 somepackage.deb

```
Probably not a good idea, but when you need the bleeding edge...

---

