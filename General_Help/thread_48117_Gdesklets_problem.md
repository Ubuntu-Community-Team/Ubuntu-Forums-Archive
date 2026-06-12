---
title: "Gdesklets problem"
date: 2005-07-11
forum: General Help
---

### Post by Morimando on 2005-07-11
One problem:
I want to view my MB temperature, nforce2 chipset. I installed the lmsensors and now fan speeds, voltage etc. is displayed in the desklet i select for it. The only thing that doesn't function is viewing mainboard/cpu temperature.
What have i missed? 
The mainboard is an ASUS A7N8X deluxe, if that's of relevance, and yes, with the ASUS-tools in Windows, temperature is displayed correctly.

[img]http://morimando.lima-city.de/screen.png[/img]

---

### Post by varunus on 2005-07-12
What are the contents of /proc/acpi/thermal_zone/THRM/ ?  This folder should list temperature information.

---

### Post by Morimando on 2005-07-12
The folder ends with /proc/acpi/thermal_zone ...there's no further folder and/or file.  [-X

---

