---
title: "Do I need acpi?"
date: 2007-06-19
forum: General Help
---

### Post by 67GTA on 2007-06-19
I am running a Gateway desktop with Intel guts. The Bios controls the temp and I never use power management. It is either on or off.  When I mark acpid for removal it wants to remove
acpi-support
gnome-power-manager
gnome-session
powermanagement-interface
I should not need any power management. What implications will removing sessions have? Do I need acpi for some reason that I'm not aware of?

---

### Post by 67GTA on 2007-06-19
Well I unchecked acpi in services and everything booted back up fine.

---

### Post by energiya on 2007-06-19
To completely remove acpi support you have to recompile the kernel, but there are some things that still need this to be activated.

---

