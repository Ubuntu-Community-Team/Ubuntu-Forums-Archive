---
title: "Acpi/rsdp Help!"
date: 2007-04-03
forum: General Help
---

### Post by galactus1 on 2007-04-03
I'm running a dual boot windows xp and kubuntu machine.  To boot windows I have to enter BIOS and enable ACPI function and to boot Ubuntu I have to enter BIOS and disable ACPI.  This get real annoying since I have to access programs (turbolister) on my windows partition and then use Kubuntu for my general computing needs.  So my question is, how do I resolve this ACPI issue without accessing BIOS every time I decide to boot to a different OS?  Thanks for the help!:)

---

### Post by cisforcojo on 2007-04-03
Edit /boot/grub/grub.conf:

Add acpi=off to the end of the line that starts with "kernel"

Should be all you need, brotha!

---

