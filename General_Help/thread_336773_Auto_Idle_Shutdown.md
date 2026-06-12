---
title: "Auto Idle Shutdown"
date: 2007-01-12
forum: General Help
---

### Post by nate010111 on 2007-01-12
Is there a way to add the option for shut down to the "Sleep type when inactive" under Power Management in Gnome?  Is there some other command line or config file solution to have the system shutdown after a idle period?

Thanks

---

### Post by tweedledee on 2007-01-13
> **nate010111 said:**
> Is there a way to add the option for shut down to the "Sleep type when inactive" under Power Management in Gnome?  Is there some other command line or config file solution to have the system shutdown after a idle period?

Thanks

I haven't tried it, but the following looks like it should work:
1) edit /etc/default/acpi-support and enable laptop mode (usually the last line, set it to true) 
2) edit /etc/laptop-mode/laptop-mode.conf, and search for the auto-hibernation section.  There is a line there about what command to execute when auto-hibernating, you could set that to the shtudown command.  Off-hand I don't remember the command, but a forum search for "how to shut down from command line" should turn it up.

Note: you might not need step 1; there may be a "no laptop mode" hibernation switch available in laptop-mode.conf, read through the file and run "man laptop-mode-tools" to see.

---

