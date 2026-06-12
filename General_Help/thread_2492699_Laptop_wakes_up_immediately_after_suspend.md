---
title: "Laptop wakes up immediately after suspend"
date: 2023-11-20
forum: General Help
---

### Post by tiaan3 on 2023-11-20
I've fallen like a rookie for the upgrade prompt from 20 to 22 and now my suspend is broken. I'm at my wits end due this as it implies i close down all windows in the evening and boot afresh in the morning which sucks.
The only hints i could find was to do
 
acpitool -w | grep -v disabled
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  2. XHC	  S3	*enabled   pci:0000:00:14.0
  5. RP01	  S3	*enabled   pci:0000:00:1c.0
  13. RP05	  S3	*enabled   pci:0000:00:1c.4
  15. RP06	  S3	*enabled   pci:0000:00:1c.5
root@waslapl:~# echo 'XHC' > /proc/acpi/wakeup
root@waslapl:~# echo 'RP01' > /proc/acpi/wakeup
root@waslapl:~# echo 'RP05' > /proc/acpi/wakeup
root@waslapl:~# echo 'RP06' > /proc/acpi/wakeup

but that helped nothing. Still wakes up immediately.

Any advise on how to troubleshoot this ?

---

