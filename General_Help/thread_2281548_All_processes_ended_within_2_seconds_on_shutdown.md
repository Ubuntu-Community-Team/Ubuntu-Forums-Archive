---
title: "All processes ended within 2 seconds on shutdown"
date: 2015-06-07
forum: General Help
---

### Post by Shane_Davies on 2015-06-07
When shuting down screen stays on "[FONT=Helvetica Neue]All processes ended within 2 seconds" I have tried a few combitions of kernel options in my grub config including:[/FONT]acpi=force
acpi=off
reboot=p
reboot=a
reboot=b
reboot=w
acpi_osi="!Windows 2013"
acpi_osi="!Windows 2012"

Lenovo W540
Ubuntu 14.04
Kernel 3.13.0-53-generic


I have tried shuting down networking. I have also tried using the onboard intel video as well as the nvidia drivers. I do not see any issues in the system logs.

Any tips on how to debug this would be greatly appreciated.

---

### Post by tgalati4 on 2015-06-09
Welcome to the forums.  So you are saying that the screen stays on for a long time?  Try removing all kernel boot options.  Shut down normally then note the time for how long the screen stays on.  It could be a BIOS setting.  What BIOS options do you have available for power management?  Try changing them and take careful notes to see how it affects shutdown behavior.

---

