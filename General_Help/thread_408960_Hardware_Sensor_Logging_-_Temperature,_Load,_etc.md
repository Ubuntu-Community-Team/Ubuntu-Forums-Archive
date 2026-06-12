---
title: "Hardware Sensor Logging - Temperature, Load, etc"
date: 2007-04-14
forum: General Help
---

### Post by disque71 on 2007-04-14
I have done a search on the forums and the web for this but wasn't able to find anything with logging capability. I have lmsensors, ksensors and x sensors installed, but none seem to support logging. 

Does anyone know of something that has a logging feature?

---

### Post by amohanty on 2007-04-14
most of the information (most not all) can also be gotten by scanning file contentsin /proc/acpi. You could write a bash script that scans them periodically and dumps the contents in an ordered way to a file.


HTH
AM

---

