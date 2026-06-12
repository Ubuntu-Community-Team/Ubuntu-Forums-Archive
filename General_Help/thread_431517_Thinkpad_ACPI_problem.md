---
title: "Thinkpad ACPI problem"
date: 2007-05-03
forum: General Help
---

### Post by ltracy on 2007-05-03
I have Ubuntu 7.04 installed on this Thinkpad R51e (Type 1844-DJU).  When I manually suspend and wake the system, everything works well, but I would really like it to suspend when the lid is closed.  I have found several how-tos for different Thinkpad models, and everything I read leads me to believe that this should be possible.

The problem appears to be that no ACPI events are reported at all.  I have tried hitting the power button, using the Fn keys, closing the lid, etc... while watching /var/log/acpid.  I have also stopped acpid and tried watching /proc/acpi/events.  Nothing appears to show up anywhere.  I'm not sure what information should be posted to help in troubleshooting this problem.

Any help/suggestions would be greatly appreciated.  I can find nothing.

---

