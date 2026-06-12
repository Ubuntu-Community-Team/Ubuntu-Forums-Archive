---
title: "Cannot shutdown or restart; Just freezes"
date: 2016-03-03
forum: General Help
---

### Post by ODBWilson on 2016-03-03
Mythbuntu: 14.04.3
Hardware: J1900

can't restart (sudo shutdown -r now, reboot, init 6) or shutdown (sudo shutdown -h now, halt, poweroff).  It just freezes with Purple Screen.  
I try to apt-get update then upgrade, the problem still exists.

And I also try all of the following boot parameters: reboot=xxxx
warm =  Don’t set the cold reboot flag
cold = Set the cold reboot flag
bios = Reboot by jumping through the BIOS (only for X86_32)
smp = Reboot by executing reset on BSP or other CPU (only for X86_32)
triple = Force a triple fault (init)
kbd = Use the keyboard controller. cold reset (default)
acpi = Use the RESET_REG in the FADT
efi = Use efi reset_system runtime service
pci = Use the so-called “PCI reset register”, CF9
force = Avoid anything that could hang.

None of the above works.

If I remove splash quite from the boot parameter, it shows:

* wait-for-state stop/wating OK
* Stop rsync daemon rsync OK
* All processes ended within 2 seconds OK
* Deactivating swap.....
* Will now restart

Just stop here forever.

Any clues?  Any other steps for diagnostic?

P.S.  
I can press Alt <Print Screen> b to reboot the system.
I can boot up with Clonezilla and reboot 
I cannot restart the system even when booting up with Mythbuntu 14.04.3 USB stick.

Thanks,
Wilson

---

### Post by mörgæs on 2016-03-03
A J1900 (Bay Trail) is so new that I wouldn't expect 14.04 to work properly. Have you tried a live boot of 15.10?

---

### Post by ODBWilson on 2016-03-04
Yup, just tried 15.10 and even 16.04.
Same thing, can't restart.
What else can I try?

---

### Post by ODBWilson on 2016-03-04
I just found that there is a OS Selection on the BIOS.
Selecting Linux solves the problem.

---

### Post by mörgæs on 2016-03-04
Good, please mark the thread 'solved'.

---

