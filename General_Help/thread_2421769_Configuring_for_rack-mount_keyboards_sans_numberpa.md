---
title: "Configuring for rack-mount keyboards sans numberpads"
date: 2019-06-26
forum: General Help
---

### Post by bcschmerker on 2019-06-26
As of 26 June 2019 I am reinstalling xubuntu™ 18.04.2-LTS on a Gateway®/Acer® DX4822-01, and I've a configuration issue with a lenovo® SK-8840 i8042 keyboard/touchpad (a similar problem exists for the same firm's SK-8845 USB 2.0 keyboard/touchpad):  I need to defeat the automatic number lock engagement, as the SK-8840 has no separate numberpad (a limitation common to many portable computers, primarily laptops and tablets).  I suspect this needs to be done in at least two Files in /etc/default; I know about /etc/default/keyboard, but cannot rule out /etc/default/grub.

The specific issue I have is with an English/Japanese installation using IBM P/N 42C0014; but this can be applied to any other SK-8840 and -8845.  How does one defeat the automatic numlock via edits to the required Files?

---

### Post by him610 on 2019-06-27
Did you consider disabling NUM-Lock in BIOS?

---

### Post by bcschmerker on 2019-06-28
> **him610 said:**
> Did you consider disabling NUM-Lock in BIOS?
**POST Setup settings do not affect this behavior, as it occurs during actual OS loading.**  Auto Numlock occurs (1) preparing to display the Login screen and (2) preparing the user homescreen.

**Update:**  It appears that /usr/bin/numlockx is part of xubuntu&#8482; and controlled at startup through /etc/default/numlockx.  Will investigate further....

---

### Post by bcschmerker on 2019-06-29
**Solution found!**  Datum changed via sudo jupp /etc/default/numlockx:  NUMLOCK = [s]auto[/s] *off*

---

