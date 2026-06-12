---
title: "dual boot and windows fast boot"
date: 2015-09-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-09-06
i know windows fast boot basically uses hibernate, which to my  understanding saves the current session to the hard drive (linux would  save this to the swap partition, while windows uses the paging file)
i setup a hardware level dual boot on a toggle switch to swap the hard drives
basically  it works the same as having 2 hot swap bays and turning only one on at a  time, just on a DPDT toggle switch (which makes it impossible to one OS  to see the other's HDD)
windows seems to never resume from it's  hibernate state, it just locks up and if you power the system off it  will not even show the BIOS splash screen till power is cut to the  system
i'm just curious how it is possible for windows to even know  another OS has been booted while it was in hibernate when it's HDD has  not had power

---

### Post by oldfred on 2015-09-06
Is this an UEFI system?

If a drive is removed, UEFI forgets its entries and that causes issues.

---

### Post by pqwoerituytrueiwoq on 2015-09-07
i am sure it supports UEFI, [http://www.asrock.com/mb/AMD/FM2A75%20Pro4-M/](http://www.asrock.com/mb/AMD/FM2A75%20Pro4-M/)
at 1st i thought UEFI BIOS was the ones with a GUI and can use a mouse, but my laptop's BIOS looks like the old kind and is UEFI

---

