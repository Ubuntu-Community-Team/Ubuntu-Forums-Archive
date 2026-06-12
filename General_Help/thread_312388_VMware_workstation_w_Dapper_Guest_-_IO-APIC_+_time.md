---
title: "VMware workstation w/ Dapper Guest - IO-APIC + timer doesn't work"
date: 2006-12-04
forum: General Help
---

### Post by Sherman.Boyd on 2006-12-04
I managed to install Dapper server on VMware 5.5.3 by using the IDE emulation instead of SCSI.  However, when I try to boot the newly installed OS, I get a kernel panic:  

MP-BIOS bug: 8254 timer not connected to IO-APIC.
Kernel panic - not syncing: IO-APIC + timer doesn't work!

The rest of the error message tells me to boot with apic=debug and then try the noapic option.

I have a dual processor machine, but set the virtual machine to a single CPU.  

Has anyone worked through this before?

---

### Post by Sherman.Boyd on 2006-12-05
I solved this by adding a second virtual processor to the virtual machine.  Hooray.

---

