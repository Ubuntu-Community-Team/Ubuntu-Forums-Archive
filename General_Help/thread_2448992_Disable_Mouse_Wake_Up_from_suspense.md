---
title: "Disable Mouse Wake Up from suspense"
date: 2020-08-17
forum: General Help
---

### Post by docdoc2 on 2020-08-17
Hello mates i have a problem and would appreciate your help.

Since Ubuntu 19.04 a tiny movement by the mouse wakes up the whole system. This is devastating as i transport my computer in a bag, if it wakes up for any reason, it could overheat or take damage otherwise or loose data.

Changes done by *acpitool* are undone at every start-up. I saw some very cumbersome scripts on the web which change */proc/acpi/wakeup *
 at every startup, but i do not think this is the right way. 

Change in* /sys/bus/usb/devices/*/power/wakeup* are also undone at next reboot. 

Does anyone know how to disable waking by mouse (and preferably, by anything else other than the power button)?

---

### Post by GhX6GZMB on 2020-08-17
It's a bit unclear in what exact mode your machine is when waking up. Just screen off or really suspend? Is it a laptop?
A least with hibernate, a mouse movement would certainly not wake up your PC.

---

### Post by docdoc2 on 2020-08-18
I mean the suspend/sleep mode. It is a laptop (asus rog). A hibernation mode is not available.

Output of acpitool -w

```
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PEG0      S4    *enabled   pci:0000:00:01.0
  2. GFX0      S4    *disabled  pci:0000:01:00.0
  3. RP09      S4    *enabled   pci:0000:00:1d.0
  4. PXSX      S4    *disabled  pci:0000:3e:00.0
  5. RP10      S4    *disabled
  6. PXSX      S4    *disabled
  7. RP11      S4    *disabled
  8. PXSX      S4    *disabled
  9. RP12      S4    *disabled
  10. PXSX      S4    *disabled
  11. RP13      S4    *disabled
  12. PXSX      S4    *disabled
  13. RP01      S4    *disabled
  14. PXSX      S4    *disabled
  15. RP02      S4    *disabled
  16. PXSX      S4    *disabled
  17. RP04      S4    *enabled   pci:0000:00:1c.3
  18. PXSX      S4    *disabled  pci:0000:04:00.0
  19. RP05      S4    *disabled  pci:0000:00:1c.4
  20. PXSX      S4    *disabled
  21. RP06      S4    *disabled
  22. PXSX      S4    *disabled
  23. RP07      S4    *disabled
  24. PXSX      S4    *disabled
  25. RP08      S4    *disabled
  26. PXSX      S4    *disabled
  27. RP17      S4    *enabled   pci:0000:00:1b.0
  28. PXSX      S4    *disabled  pci:0000:02:00.0
  29. RP18      S4    *disabled
  30. PXSX      S4    *disabled
  31. RP19      S4    *disabled
  32. PXSX      S4    *disabled
  33. RP20      S4    *disabled
  34. PXSX      S4    *disabled
  35. RP14      S4    *disabled
  36. PXSX      S4    *disabled
  37. RP15      S4    *disabled
  38. PXSX      S4    *disabled
  39. RP16      S4    *disabled
  40. PXSX      S4    *disabled
  41. XHC      S3    *enabled   pci:0000:00:14.0
  42. XDCI      S4    *disabled
  43. HDAS      S4    *disabled  pci:0000:00:1f.3
  44. SLPB      S4    *enabled   platform:PNP0C0E:00

```

41. XHC is the mouse. I would like to disable it permanently, and maybe also the other enabled entries.

---

