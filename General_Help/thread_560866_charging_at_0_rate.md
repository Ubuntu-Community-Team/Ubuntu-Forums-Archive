---
title: "charging at 0 rate"
date: 2007-09-26
forum: General Help
---

### Post by nonewmsgs on 2007-09-26
my problem is just a wtf


william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 94%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 61.0 degrees C
  AC Adapter 1: on-line
william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 95%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 62.0 degrees C
  AC Adapter 1: on-line
william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 95%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 60.0 degrees C
  AC Adapter 1: on-line
william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 95%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 61.0 degrees C
  AC Adapter 1: on-line
william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 98%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 60.0 degrees C
  AC Adapter 1: on-line
william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 98%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 59.0 degrees C
  AC Adapter 1: on-line
william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 98%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 60.0 degrees C
  AC Adapter 1: on-line
william@william-laptop-hp900:~$ acpi -V
     Battery 1: charging, 99%, charging at zero rate - will never fully charge.
     Thermal 1: ok, 62.0 degrees C
  AC Adapter 1: on-line

---

### Post by tstavely on 2007-11-26
Yeah, same here.  My replacement battery for a thinkpad x30 reports more power than it's design capacity, and is apparently always charging when plugged into the wall, though at 0 rate once it's up in the high 90s %.  Is there any way to trick the battery management software to count some number as fully charged so the phantom charging will stop?

---

### Post by schierly on 2007-12-03
> **tstavely said:**
> Yeah, same here.  My replacement battery for a thinkpad x30 reports more power than it's design capacity, and is apparently always charging when plugged into the wall, though at 0 rate once it's up in the high 90s %.  Is there any way to trick the battery management software to count some number as fully charged so the phantom charging will stop?

I have the same problem in an Acer latop! Does anybody know what does it really mean?

In my case I replaced my old battery with a new one which has a higher capacity. Does it mean, it can only charge up to the capacity of the old battery?
In my case it's not allways charging, it stops at 100% and starts maybe again at about 95%.

---

### Post by metalheart on 2007-12-03
It's sometimes recommended to do couple full charge/discharge cycles to get the original capacity back (or most of it).

---

