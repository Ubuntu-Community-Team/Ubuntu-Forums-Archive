---
title: "Resume from Suspend using keyboard or mouse"
date: 2007-12-30
forum: General Help
---

### Post by rsf33 on 2007-12-30
I installed Ubuntu 7.10 on my HP a6200n desktop PC successfully. I am using the PS/2 keyboard that came with the PC, and a Kensington USB wireless mouse.

When I suspend the computer (using the suspend key on the keyboard, or clicking on Suspend in the GNOME desktop) it goes to sleep just fine. I can wake up the computer by hitting its power button, but I cannot wake it up by pressing keys on the PS/2 keyboard or moving the USB wireless mouse. Plugging in a PS/2 mouse and moving that doesn't wake the computer up either.

Is there a way to configure Ubuntu to allow a key press or mouse movement to wake the computer so I don't have to climb under the desk to hit the power button each time? I did try rebooting the computer and entering its BIOS setup utility, but I don't see any options there for power management. (The BIOS appears to be Phoenix AwardBIOS.)

Any help would be greatly appreciated.

---

### Post by simoncullen on 2008-02-16
Have a look here: [https://lists.linux-foundation.org/pipermail/linux-pm/2007-November/015551.html](https://lists.linux-foundation.org/pipermail/linux-pm/2007-November/015551.html)

"echo "USB1" > /proc/acpi/wakeup" worked for me!

Simon

---

### Post by NEI on 2008-03-04
> "echo "USB1" > /proc/acpi/wakeup" worked for me!

I get a "Permission denied" when doing this! Even with sudo... Why? What am I doing wrong?

---

