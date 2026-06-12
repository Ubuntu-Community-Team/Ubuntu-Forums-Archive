---
title: "Laptop not resuming from suspend on lid open"
date: 2014-02-04
forum: General Help
---

### Post by roudy1989 on 2014-02-04
Hi,

there are several threads out there about this topic but I promise I did some research before I am posting here ;-)

In Windows closing the lid makes it going to sleep and opening it makes it resuming.

I am using Ubuntu 13.10 on my Samsung Series 7 Chronos 700Z3A-S02DE. When I close the lid the laptop goes to sleep, but on lid open it remains sleeping until I press the power button to wake it up. My goal is to make it waking up upon opening the lid. Using ```
acpi_listen
``` I see that it fires and recognizes the events for lid close and open and /proc/acpi/button/lid/LID0/state shows the correct state for each lid position. With ```
acpid -d -f -l
``` I see that those events trigger /etc/acpi/events/. I wrote an event that matches lid close/open and calls pm-suspend. But this does not make the laptop resume.
I also uncommented the lines in /etc/systemd/logind.conf regarding hibernate and suspend. But this does not work either.

So my problem is that the system receivs and understand those ACPI events triggered from the lid actions. But LID0 is not configured as /etc/acpi/wakeup device. Nor echoing it into the file does make it appearing there. So I am at the end of my knowledge and understanding of the ACPI event handling.

I've already tried to pass different acpi_osi Strings with grub but the ACPI table does not change nor make it any difference for the suspend/resume problem.

Does someone has a hint for me how to dig further into the problem? I'd appreciate this!

---

### Post by roudy1989 on 2014-02-06
Bump it up :-)

---

### Post by roudy1989 on 2014-02-10
Is there really noone with some insight in this process?

---

