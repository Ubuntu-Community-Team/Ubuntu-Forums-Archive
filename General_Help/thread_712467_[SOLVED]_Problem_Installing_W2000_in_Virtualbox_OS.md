---
title: "[SOLVED] Problem Installing W2000 in Virtualbox OSE"
date: 2008-03-01
forum: General Help
---

### Post by gcornett on 2008-03-01
The Windows 2000 installer keeps repeating the Setup Wizard over and over.  I tried powering off the virtual machine and restarting the installation from scratch.  Same problem.  If I reboot without the CD it still restarts the Wizard and goes through the whole thing again.  

Configuration of the virtual machine is:
OS Type Windows 2000
Base Mem  168 MB
Video Mem     8 MB
Hard Drive     4 Gig
ACPI            Enabled
IO APIC        Disabled
Network       Enabled, NAT
Serial          Disabled
Shared Folders   None

No Guest Additions.  Haven't got that far.

---

### Post by RD1 on 2008-03-01
Same problem here, That's why I opted for VMWare instead.

---

### Post by gcornett on 2008-03-02
Solved it.  Found a thread on the virtualbox forum that pointed me to the Virtualbox User Manual Section 11.2.2.

Seems that there is a bug in the Win 2000 installer that causes a race condition if the disk access is too fast and corrupts the data.

---

