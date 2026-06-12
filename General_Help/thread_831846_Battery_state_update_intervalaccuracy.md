---
title: "Battery state update interval/accuracy"
date: 2008-06-17
forum: General Help
---

### Post by dnaxx on 2008-06-17
Hello, 

I am using "cat /proc/acpi/battery/BAT0/*" to get the current battery state but the state is update only every 5 seconds (approx.). 
a.) is there a way to change the update interval?
b.) are there alternative linux tools to get the current power consumption?

Regards,

---

### Post by sdennie on 2008-06-17
a) Is there a specific reason you want to change this?  It's probably provided by the BIOS so, I'm not sure if the granularity can be adjusted.

b) Are you looking for command line or gui tools?  If command line, a simple way to get basic information is to simply type:

```

acpi

```

If you are looking for a GUI application, check System->Preferences->Power Management and, in the last tab, make sure you set it so you can at least see the battery icon sometimes.  If you left click on the battery icon in the panel and select your battery, it should give you information similar to what you see from /proc/acpi.

---

